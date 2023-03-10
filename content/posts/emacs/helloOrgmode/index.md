+++
title = "Hello Org-mode"
date = 2023-01-28T18:00:00+08:00
lastmod = 2023-02-09T21:35:00+08:00
tags = ["Org-mode"]
categories = ["Emacs"]
draft = false
bookToc = true
bookFlatSection = false
bookCollapseSection = false
+++

## <span class="section-num">1</span> Hello Org-mode {#hello-org-mode}

This article is written to show how to write and run codes in Org-mode. <br/>


## <span class="section-num">2</span> Codes in Org-babel {#codes-in-org-babel}


### <span class="section-num">2.1</span> Shell {#shell}

```org
#+begin_src shell :results output :exports both
tree
#+end_src
```

```org
#+RESULTS:
#+begin_example
.
├── R.png
├── babel-stable-985
├── csv.csv
├── f90.f90
├── gnuplot.png
├── org.org
├── snoopy.png
└── tikz.png

1 directory, 7 files
#+end_example
```


### <span class="section-num">2.2</span> Emacs-lisp {#emacs-lisp}

```org
#+begin_src emacs-lisp :results output :exports both
(princ (+ 1 2 3))
(princ "\n")
(princ (* 1 2 3))
#+end_src
```

```org
#+RESULTS:
: 6
: 6
```


### <span class="section-num">2.3</span> C++ {#c-plus-plus}

```org
#+begin_src cpp :results output :exports both
#include <iostream>
using namespace std;
int main() {
  cout << "Hello, C++!" << endl;
  return 0;
}
#+end_src
```

```org
#+RESULTS:
: Hello, C++!
```


### <span class="section-num">2.4</span> Fortran {#fortran}

```org
#+begin_src fortran :exports none :tangle fortran.f90 :comments link
program hello
   implicit none
   write (*, *) 'Hello Fortran!'
end program hello
#+end_src
```

```org
#+RESULTS:
: Hello Fortran!
```


### <span class="section-num">2.5</span> Julia {#julia}

```org
#+begin_src julia :results output :tangle julia.jl :comments link
function greet()
  print("Hello Julia!")
end
greet()
#+end_src
```

```org
#+RESULTS:
: greet (generic function with 1 method)
: Hello Julia!
```


### <span class="section-num">2.6</span> Python {#python}

```org
#+begin_src python :session :results output :exports both :tangle py.py :comments link
import math
print("Hello, Python!")
print(math.pi)
#+end_src
```

```org
#+RESULTS:
: Hello, Python!
: 3.141592653589793
```


### <span class="section-num">2.7</span> Octave {#octave}

```org
#+begin_src octave :session :results output :exports both
n = [1:10];
x = 5*n;
ans = x
#+end_src
```

```org
#+RESULTS:
:
: octave> ans =
:
:     5   10   15   20   25   30   35   40   45   50
```


### <span class="section-num">2.8</span> R {#r}

Use the `session: *code buffer name*` so that different R code blocks can share the data. The default buffer name is "R". <br/>

```org
#+begin_src R :session *RCode* :results output :exports both :tangle R.R :comments link
data <- read.csv("csv.csv")
print(data)
#+end_src
```

```org
#+RESULTS:
:   id   name            url likes
: 1  1 Google www.google.com   111
: 2  1 Google www.google.com   111
: 3  1 Google www.google.com   111
```

```org
#+begin_src R :session *RCode*:file R.png :results output graphics file :exports both :tangle R.R :comments link
library(lattice)
xyplot(1:10 ~ 1:10)
#+end_src
```

{{< figure src="R.png" caption="<span class=\"figure-number\">Figure 1: </span>R code" >}} <br/>


### <span class="section-num">2.9</span> Gnuplot {#gnuplot}

```org
#+begin_src gnuplot :session :file gnuplot.png :exports both
plot sin(x) + cos(x)
#+end_src
```

{{< figure src="gnuplot.png" caption="<span class=\"figure-number\">Figure 2: </span>Gnuplot" >}} <br/>


### <span class="section-num">2.10</span> Tikz {#tikz}

```org
#+name: tikz example
#+header: :file "./tikz.png"
#+header: :results output graphics file :exports both :fit yes :border 0cm
#+header: :imagemagick t :iminoptions -density 300
#+header: :imoutoptions -geometry 600 -flatten
#+header: :headers '("\\usepackage{tikz} \\usetikzlibrary{backgrounds, quotes, angles, intersections, calc}")
#+begin_src latex
\begin{tikzpicture}
  % Your codes.
\end{tikzpicture}
#+end_src
```

```org
#+caption: Tikz codes
#+name: tikz example
#+header: :file "./tikz.png"
#+header: :results output graphics file :exports both :fit yes :border 0cm
#+header: :imagemagick t :iminoptions -density 300
#+header: :imoutoptions -geometry 600 -flatten
#+header: :headers '("\\usepackage{tikz} \\usetikzlibrary{backgrounds, quotes, angles, intersections, calc}")
#+begin_src latex
\tikzstyle{load}   = [ultra thick,-latex]
\tikzstyle{stress} = [-latex]
\tikzstyle{dim}    = [latex-latex]
\tikzstyle{axis}   = [-latex,black!55]
% Drawing Views
\tikzstyle{isometric}=[x={(0.710cm,-0.410cm)},y={(0cm,0.820cm)},z={(-0.710cm,-0.410cm)}]
\tikzstyle{dimetric} =[x={(0.935cm,-0.118cm)},y={(0cm,0.943cm)},z={(-0.354cm,-0.312cm)}]
\tikzstyle{dimetric2}=[x={(0.935cm,-0.118cm)},z={(0cm,0.943cm)},y={(+0.354cm,+0.312cm)}]
\tikzstyle{trimetric}=[x={(0.926cm,-0.207cm)},y={(0cm,0.837cm)},z={(-0.378cm,-0.507cm)}]
\begin{tikzpicture}
	\node (origin) at (0,0) {}; % shift relative baseline
	\coordinate (O) at (2,3);
	\draw[fill=gray!10] (O) circle (1);
	\draw[fill=white] (O) circle (0.75) node[below,yshift=-1.125cm] {Signpost Cross Section};
	\draw[dim] (O) ++(-0.75,0) -- ++(1.5,0) node[midway,above] {$d_i$};
	\draw[dim] (O) ++(-1,1.25) -- ++(2,0) node[midway,above] {$d_o$};
	\foreach \x in {-1,1} {
			\draw (O) ++(\x,0.25) -- ++(0,1.25);
		}
\end{tikzpicture}
\begin{tikzpicture}[dimetric2]
	\coordinate (O) at (0,0,0);
	\draw[axis] (O) -- ++(6,0,0) node[right] {$x$};
	\draw[axis] (O) -- ++(0,6,0) node[above right] {$y$};
	\draw[axis] (O) -- ++(0,0,6) node[above] {$z$};
	\draw[fill=gray!50] (0,0,-0.5) circle (0.5);
	\fill[fill=gray!50] (-0.46,-0.2,-0.5) -- (0.46,0.2,-0.5) -- (0.46,0.2,0) -- (-0.46,-0.2,0) -- cycle;
	\draw[fill=gray!20] (O) circle (0.5);
	\draw (0.46,0.2,-0.5) -- ++(0,0,0.5) node[below right,pos=0.0] {Fixed Support};
	\draw (-0.46,-0.2,-0.5) -- ++(0,0,0.5);
	\draw[fill=gray!10] (O) circle (0.2);
	\fill[fill=gray!10] (-0.175,-0.1,0) -- (0.175,0.1,0) -- ++(0,0,4) -- (-0.175,-0.1,4) -- cycle;
	\draw (-0.175,-0.1,0) -- ++(0,0,4);
	\draw (0.175,0.1,0) -- ++(0,0,4) node[right,midway] {Steel Post};
	\draw (4,0,3.95) -- ++(0,0,-1);
	\foreach \z in {0.5,0.75,...,5} {
			\draw[-latex] (-2*\z/5-0.2,0,\z) -- (-0.2,0,\z);
		}
	\draw[load] (0,0,4) -- ++(0,0,-1.25) node[right,xshift=0.1cm] {$F_{z1}$};
	\draw[fill=gray!20] (-0.25,-0.25,5) -- (4,-0.25,5) -- (4,+0.25,5) -- (-0.25,+0.25,5) -- cycle;
	\draw[fill=gray!50] (+4.00,-0.25,4) -- (4,+0.25,4) -- (4,+0.25,5) -- (+4.00,-0.25,5) -- cycle;
	\draw[fill=gray!10] (-0.25,-0.25,4) -- (4,-0.25,4) -- (4,-0.25,5) -- (-0.25,-0.25,5) -- cycle;
	\draw (4.05,0,4) -- ++(1,0,0);
	\draw (4.05,0,5) -- ++(1,0,0);
	\draw[dim] (4.5,0,0) -- ++(0,0,4) node[midway,right] {$h_1$};
	\draw[dim] (4.5,0,4) -- ++(0,0,1) node[midway,right] {$h_2$};
	\draw[dim] (0,0,3.4) -- ++(4,0,0) node[midway,below] {$b_2$};
	\coordinate (P) at (2,-0.25,4.5);
	\draw (P) -- ++(0,0,0.25);
	\draw (P) -- ++(0.25,0,0);
	\draw[dim] (2.125,-0.25,4.5) -- ++(0,0,-0.5) node[midway,right] {$z_1$};
	\draw[dim] (2,-0.25,4.625) -- ++(-2,0,0) node[midway,below] {$x_1$};
	\draw[load] (2,-2.45,4.5) -- ++(0,2.2,0) node[pos=0.0,right,xshift=0.08cm] {$F_{y1}$};
	\draw[axis,dashed,-] (O) -- (0,0,5);
	\draw (0,0,5.5) -- ++(4,0,0) node[midway,above] {$w_{z}$};
	\foreach \x in {0,0.25,...,4} {
			\draw[-latex] (\x,0,5.5) -- ++(0,0,-0.5);
		}
	\draw (-0.2,0,0) -- ++(-2,0,5) node[above,xshift=0.5cm] {$w_{x}=\frac{z}{h_1+h_2} w_0$};
\end{tikzpicture}
#+end_src
```

{{< figure src="tikz.png" caption="<span class=\"figure-number\">Figure 3: </span>[Tikz codes](https://texample.net/tikz/examples/signpost/)" >}} <br/>


## <span class="section-num">3</span> Others {#others}


### <span class="section-num">3.1</span> HTML and CSS {#html-and-css}

You can add CSS to make HTML more readable. <br/>

```org
#+OPTIONS: html-style:nil
#+HTML_HEAD: <link rel="stylesheet" type="text/css" href="PATH/org.css"/>
```


### <span class="section-num">3.2</span> Tangle and detangle {#tangle-and-detangle}

Add `tangle: PATH/python.py` and `comment: link` above the code block. Use `C-c C-v t` to tangle codes. Open the code file in Emacs and type `M-x org-babel-detangle` to update the code block in the Org file. <br/>
See [2.6](#python) and [2.8](#r). <br/>


### <span class="section-num">3.3</span> Auto number the picture {#auto-number-the-picture}

You can use the `#+caption` function to assign titles to figures or codes. However, there exists a [bug](https://github.com/kaushalmodi/ox-hugo/issues/686) in org 9.6 where the figures will get the same number in the output file. You need to modify them manually. This bug has been fixed in org 9.6.1. <br/>
If you use doom emacs, you can add `(unpin! org)` in `~/.doom.d/packages.el` and input `doom upgrade` in the shell command to update the org. <br/>

```org
#+caption: [[https://en.wikipedia.org/wiki/Peanuts][Snoopy]]
[[file:snoopy.png]]
```

{{< figure src="snoopy.png" caption="<span class=\"figure-number\">Figure 4: </span>[Snoopy](https://en.wikipedia.org/wiki/Peanuts)" >}} <br/>


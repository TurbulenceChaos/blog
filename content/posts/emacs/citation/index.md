+++
title = "Citations"
date = 2023-02-03T23:00:00+08:00
lastmod = 2023-02-04T01:50:10+08:00
categories = ["Emacs"]
draft = false
bookToc = true
bookFlatSection = false
bookCollapseSection = false
+++

## Paper {#paper}

Refer to <a href="#citeproc_bib_item_1">[1]</a> for more information. <br/>
Also I should mention <a href="#citeproc_bib_item_2">[2]</a>. <br/>

## References

<style>.csl-left-margin{float: left; padding-right: 0em;}
 .csl-right-inline{margin: 0 0 0 1em;}</style><div class="csl-bib-body">
  <div class="csl-entry"><a id="citeproc_bib_item_1"></a>
    <div class="csl-left-margin">[1]</div><div class="csl-right-inline">R. A. Ibrahim, <i>Liquid Sloshing Dynamics: Theory and Applications</i>, First. Cambridge University Press, 2005. doi: <a href="https://doi.org/10.1017/CBO9780511536656">10.1017/CBO9780511536656</a>.</div>
  </div>
  <div class="csl-entry"><a id="citeproc_bib_item_2"></a>
    <div class="csl-left-margin">[2]</div><div class="csl-right-inline">O. M. Faltinsen and A. N. Timokha, <i>Sloshing</i>. New York, NY: Cambridge University Press, 2009.</div>
  </div>
</div>


## Three exporting formats {#three-exporting-formats}

{{< tabs "paper" >}}

{{< tab "org to LaTex" >}}

Command: `C-c C-e l l` <br/>

```org
#+BIBLIOGRAPHY: PATH/paper.bib
#+CITE_EXPORT: biblatex ieee
* Paper
Refer to [cite:@ibrahim_2005_LiquidSloshingDynamicsTheoryApplications] for more information.
Also I should mention [cite:@faltinsen_2009_Sloshing].

#+PRINT_BIBLIOGRAPHY:
```

{{< /tab >}}

{{< tab "org to HTML" >}}

Command: `C-c C-e h h` <br/>

```org
#+BIBLIOGRAPHY: PATH/paper.bib
#+CITE_EXPORT: csl ieee.csl
* Paper
Refer to [cite:@ibrahim_2005_LiquidSloshingDynamicsTheoryApplications] for more information.
Also I should mention [cite:@faltinsen_2009_Sloshing].

* Preference
#+PRINT_BIBLIOGRAPHY:
```

{{< /tab >}}

{{< tab "ox-odt: odt to docx" >}}

Add the code below in `~.doom.d/config.el` file. <br/>

```org
#+begin_src emacs-lisp
(after! org
  (setq org-odt-preferred-output-format "docx"))
#+end_src
```

Then use `sudo apt-get install libreoffice-common` and `sudo apt-get install libreoffice-write` in ubuntu to install libreoffice. <br/>

Use command: `C-c C-e o o` to convert org to docx. <br/>

```org
#+BIBLIOGRAPHY: PATH/paper.bib
#+CITE_EXPORT: csl ieee.csl
* Paper
Refer to [cite:@ibrahim_2005_LiquidSloshingDynamicsTheoryApplications] for more information.
Also I should mention [cite:@faltinsen_2009_Sloshing].

*Preference
#+PRINT_BIBLIOGRAPHY:
```

{{< /tab >}}

{{< tab "pandoc: org to docx" >}}

Use `sudo apt insatll pandoc` in ubuntu to install pandoc. <br/>
Add `#+OTD_APP: docx` in org file. If you do not add this sentence, pandoc will not export docx with citations. <br/>
Then use command: `M-x org-pandoc-export-to-docx` to convert org to docx. <br/>

```org
#+OTD_APP: docx
#+BIBLIOGRAPHY: PATH/paper.bib
#+CITE_EXPORT: csl ieee.csl
* Paper
Refer to [cite:@ibrahim_2005_LiquidSloshingDynamicsTheoryApplications] for more information.
Also I should mention [cite:@faltinsen_2009_Sloshing].

*Preference
#+PRINT_BIBLIOGRAPHY:
```

{{< /tab >}}

{{< /tabs >}}


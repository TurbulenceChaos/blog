+++
title = "GTD"
date = 2023-01-30T02:00:00+08:00
lastmod = 2023-01-30T02:06:39+08:00
tags = ["Org-mode"]
categories = ["Emacs"]
draft = false
bookToc = true
bookFlatSection = false
bookCollapseSection = false
+++

## 1 Highlight `DONE` and `TODO` in HUGO {#1-highlight-done-and-todo-in-hugo}

Add the following codes in Org-mode file so that `TODO` and `DONE` can be highlighted in HUGO.

<style>
/* *** Org table-caption set to be in the middle of the page*/
.table-caption {
text-align: center;
}
.org-todo {
font-size: 0.8em;
font-weight: 700;
}
/* *** Org TODO set to TODO state */
.org-todo.todo {
color: #e60000;
}
/* *** Org TODO set to DONE state */
.org-todo.done {
color: green;
}
</style>

```org
#+begin_export html
.org-todo {
font-size: 0.8em;
font-weight: 700;
}
/* *** Org TODO set to TODO state */
.org-todo.todo {
color: #e60000;
}
/* *** Org TODO set to DONE state */
.org-todo.done {
color: green;
}
</style>
#+end_export
```


## 2 Time tracing {#2-time-tracing}

{{< columns >}}


### ONE <code>[100%]</code> {#one}


#### <span class="org-todo done DONE">DONE</span> head1 {#head1}


#### <span class="org-todo todo TODO">TODO</span> head2 {#head2}


#### <span class="org-todo todo TODO">TODO</span> head3 {#head3}


### TWO <code>[66%]</code> {#two}


#### <span class="org-todo todo TODO">TODO</span> head3 {#head3}


#### <span class="org-todo done DONE">DONE</span> head4 {#head4}


#### <span class="org-todo done DONE">DONE</span> head5 {#head5}


### <span class="org-todo done DONE">DONE</span> THREE <code>[100%]</code> {#three}

-   [X] 111
-   [X] 222
-   [X] 333

<--->

<div class="table-caption">
  <span class="table-number">Table 1:</span>
  Clock summary at <span class="timestamp-wrapper"><span class="timestamp">[2023-01-30 Mon 01:00]</span></span>
</div>

| Headline               | Time     |      |
|------------------------|----------|------|
| **Total time**         | **0:21** |      |
| 2 Time tracing         | 0:21     |      |
| &ensp;&ensp;ONE [100%] |          | 0:01 |
| &ensp;&ensp;TWO [66%]  |          | 0:20 |

{{< /columns >}}

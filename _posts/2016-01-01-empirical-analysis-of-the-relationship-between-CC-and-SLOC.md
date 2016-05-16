---
published: true
title: Empirical analysis of the relationship between CC and SLOC
author: Davy Landman
authorlink: "http://homepages.cwi.nl/~landman/"
layout: post
---

Check out these two related articles on the empirical relation between the CC and SLOC source code metrics.

```
@ARTICLE{jsep2015-landman,
  author = { Davy Landman and Alexander Serebrenik and Eric Bouwers and Jurgen J. Vinju },
  title = { {Empirical analysis of the relationship between CC and SLOC in a large corpus of Java methods and C functions} },
  journal = { Journal of Software: Evolution and Process },
  year = { 2015 },
  doi = { 10.1002/smr.1760 },
  fulltext  = "http://homepages.cwi.nl/~landman/docs/Landman2015-ccsloc-jsep2015-preprint.pdf",
  datalink = { http://homepages.cwi.nl/~landman/jsep2015/ },
}

@INPROCEEDINGS{Landman2014,
  author = { Davy Landman and Alexander Serebrenik and Jurgen J. Vinju },
  title = { {Empirical analysis of the relationship between CC and SLOC in a large corpus of Java methods} },
  booktitle = { 30th IEEE International Conference on Software Maintenance and
  Evolution, ICSME 2014 },
  year = { 2014 },
  datalink = { http://homepages.cwi.nl/~landman/icsme2014/ },
  fulltext= "http://homepages.cwi.nl/~landman/docs/Landman2014-ccsloc-icsme2014-preprint.pdf"
}
```

Measuring the internal quality of source code is one of the traditional 
    goals of making software development into an engineering discipline. 
    Cyclomatic Complexity (CC) is an often used source code quality metric, next 
    to Source Lines of Code (SLOC). However, the use of the CC metric is 
    challenged by the repeated claim that CC is redundant with respect to SLOC 
    due to strong linear correlation.


    We conducted an extensive literature study of the CC/SLOC correlation results. 
    Next, we tested correlation on large Java (17.6 M methods) and C (6.3 M 
    functions) corpora. Our results show that linear correlation between SLOC and CC 
    is only moderate as caused by increasingly high variance. We further observe 
    that aggregating CC and SLOC as well as performing a power transform improves 
    the correlation.

    Our conclusion is that the observed linear correlation between CC and SLOC 
    of Java methods or C functions is not strong enough to conclude that CC is 
    redundant with SLOC. This conclusion contradicts earlier claims from 
    literature, but concurs with the widely accepted practice of measuring of CC 
    next to SLOC.

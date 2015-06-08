---
layout: default
title: PLDI 2015 Workshop 
published: true
---

[Rascal]:http://www.rascal-mpl.org/
[http://www.rascal-mpl.org/]:http://www.rascal-mpl.org/

# Tutorial: Program Analysis and Transformation with Rascal (PLDI 2015)

This is the landing page for the tutorial "Program Analysis and Transformation
with Rascal" that is being given this year at PLDI 2015 on the afternoon of
Saturday, January 13th. More information will be added to this page soon. If
you are interested in learning more about and/or downloading Rascal, you can
visit the Rascal homepage at [http://www.rascal-mpl.org/].

## Tutorial Abstract

[Rascal] is a meta-programming language that combines a familiar Java-like
syntax with a powerful collection of built-in data types and language
features, including relations with relational algebra operators, extensive
support for pattern matching, higher-order functions, and fix-point
computation. Rascal is currently being used to develop program analysis tools
for languages such as Java, PHP, and Lua; to create domain-specific languages
for domains such as gaming and digital forensics; to create large-scale
program transformations; and to extract metrics across large collections of
software systems.

In this tutorial, we will first create a small language and define several
elementary operations, like counting operator uses and performing simple
program transformations. Next we will introduce the Metrics Meta Model (M3),
which models information related to source code, and show how it can be used
to define operations on Java and PHP such as measuring methods per class,
counting cast statements, measuring if-nesting and computing the McCabe
complexity. Finally, we will sketch a larger scale program transformation on
real Java code: how to convert code using the visitor pattern into code that
uses the interpreter pattern. The tutorial concludes with a brief sketch of
current and future developments of the Rascal language and its ecosystem.

*Expected Audience:* This tutorial will be appropriate for both researchers
and practitioners. Previous experience with tools for computing software
metrics and for performing analysis and transformation is recommended but is
not mandatory.

## The Presenters

This tutorial will be presented by (in alphabetical order):

[http://www.cs.ecu.edu/hillsma/]:http://www.cs.ecu.edu/hillsma/
[http://homepages.cwi.nl/~paulk/]:http://homepages.cwi.nl/~paulk/
[http://homepages.cwi.nl/~jurgenv/]:http://homepages.cwi.nl/~jurgenv/

* Mark Hills (East Carolina University): [http://www.cs.ecu.edu/hillsma/]
* Paul Klint (Centrum Wiskunde & Informatica): [http://homepages.cwi.nl/~paulk/]
* Jurgen J. Vinju (Centrum Wiskunde & Informatica): [http://homepages.cwi.nl/~jurgenv/]

## Supplementary Materials

A number of papers about and/or using Rascal have been published over the last
several years. Here is a sampling that may be of interest to the target
audience for this tutorial.

* P. Klint, T. van der Storm and J.J. Vinju, EASY Meta-Programming with RASCAL, Proceedings of the Summer School on Generative and Transformational Techniques in Software Engineering 2009, Series: Lecture Notes in Computer Science, Vol. 6491, pp. 222 - 289. Springer, 2011, [PDF](http://homepages.cwi.nl/~paulk/publications/rascal-gttse-final.pdf)

* P. Klint, J.J. Vinju, T. van der Storm, RASCAL: A Domain Specific Language for Source Code Analysis and Manipulation, IEEE International Workshop on Source Code Analysis and Manipulation, 168-177, IEEE Computer Society, 2009, [PDF](http://homepages.cwi.nl/~paulk/publications/rascal-scam-09.pdf)

* M. Hills, P. Klint, T. van der Storm, and J. J. Vinju, A Case of Visitor versus Interpreter Pattern, Proceedings of TOOLS 2011, volume 6705 of LNCS, pages 228-243. Springer, 2011, [PDF](http://www.cs.ecu.edu/hillsma/publications/hills-klint-storm-vinju-2011-tools.pdf)

* M. Hills, P. Klint, and J. J. Vinju, Scripting a Refactoring with Rascal and Eclipse, Proceedings of WRT 2012, pages 40-49. ACM, 2012, [PDF](http://www.cs.ecu.edu/hillsma/publications/hills-klint-vinju-2012-wrt.pdf)

* M. Hills, P. Klint, and J. J. Vinju, An Empirical Study of PHP Feature Usage: A Static Analysis Perspective, Proceedings of ISSTA 2013, pages 325-335. ACM, 2013, [PDF](http://www.cs.ecu.edu/hillsma/publications/php-feature-usage.pdf)

* A. Izmaylova, P. Klint, A. Shahi, and J. J. Vinju, M3: An Open Model for Measuring Code Artifacts, [PDF](http://arxiv.org/pdf/1312.1188v1)

* M. Hills and P. Klint, PHP AiR: Analyzing PHP Systems with Rascal, Proceedings of CSMR/WCRE 2014 Tools, pages 454-457. IEEE, 2014, [PDF](http://www.cs.ecu.edu/hillsma/publications/phpair-csmr.pdf)

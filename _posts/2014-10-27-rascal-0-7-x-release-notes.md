---
layout: post 
published: true
author: Jurgen Vinju
authorlink: http://homepages.cwi.nl/~jurgenv
title: "Rascal 0.7.x release notes"
---

In this post we report on the Rascal release 0.7.0. We expect a number of patch releases as well, which we report on by updating this post (at its end) when necessary. The Rascal release includes the following main components:

* Parser and interpreter: parsing and running Rascal programs
* Parser generator: generating parsers for programming languages and domain specific languages
* Eclipse plugin: an IDE for Rascal
* Eclipse plugin generator for DSLs: an IDE generator based on Rascal programs
* Rascal commandline shell: to run Rascal independently from Eclipse
* Standard library: utilities for programming in Rascal, including several (stable) programming language front-ends and general analysis facilities.

Compared to 0.6.x the 0.7 release is mainly a bug fix release, with a number of extensions to the libraries and one new language feature. 

* The new language feature is keyword parameters for both functions and data constructors. 
* In terms of library funcionality the big new things is *M3*, a common intermediate format for facts about source code. This includes a standard set of relations (containment, def/use, etc.) and a preferred way of modeling abstract syntax trees.

### M3

### Keyword parameters

### Looking forward to the 0.8.x, 0.9.x and 1.0 releases

The 0.8 release is planned with:

* Re-implemented general top-down parsing algorithm with on-demand lexing
* Fast regular expressions and better language integrated pattern matching
* Concrete syntax features completed and streamlined due to new parser integration
* Standard library component for communicating with SMT solvers easily

The 0.9 release is planned with:

* Keyword parameters replacing annotations completely
* New Figure library based on javascript

The 1.0 release is a big bang release which includes the following new components which have been developed over the last two years:

* The Rascal type checker
* Rascal compiler to RVM
* RVM interpreter

In 1.0 the old Rascal interpreter will still be included, but from here on its usage will be deprecated. We will be working to switch the IDE support to using the new infra-structure for a while and when this is finished the interpreter will not be released any longer. Note that this does not mean that we will not have a REPL for Rascal anymore. We will always have a REPL.

### Patch releases

* Patch 0.7.1. includes an update to the documentation on M3
* Patch 0.7.2. bug fixes
* Patch 0.7.3. bug fixes and memory optimizations (more than 50%)

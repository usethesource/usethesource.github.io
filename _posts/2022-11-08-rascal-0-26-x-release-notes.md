---
layout: post 
published: true
author: "Jurgen J. Vinju"
authorlink: "http://www.rascal-mpl.org"
title: "Rascal 0.26.x release notes"
---

In this post we report on the Rascal release 0.26.x

<!--truncate-->

## Release 0.26.5 - November 8, 2022

* the documentation compiler, a.k.a. course compiler, a.k.a. tutor, was separated into its own top-level project called [rascal-tutor](https://www.github.com/usethesource/rascal-tutor) 
* 80% of the documentation was reviewed and fixed
   * ported from asciidoctor to Docusaurus markdown 
   * using new features of the new tutor compiler 
   * all code examples run again
   * all broken links fixed
   * broken rascal-eclipse library documentation moved to the rascal-eclipse project
* in `util::Benchmark` several overloaded functions were renamed to fix static typing issues.
* in `IO` read and write functions with positional encoding parameters were made `@deprecated` in favor of their simpler counterparts with keywordparameters for the encoding.
* rascal no longer depends on jruby or asciidoctor 
* `Node::unsetRec` was optimized which led to a large speed improvement of the parser generator
* added `PATH:///` logical file resolver which works well in combination with `util::ShellExec` for finding executables in the system `PATH` variable to run.
* `util::ShellExec` can now deal with `loc` values anywhere the API expects a file location. This goes also for file parameters to executables. Before they are passed to the executable, Rascal finds or creates and absolute file system path with the contents of the file.


## Release 0.25.x 

Release 0.25.x were intermediate releases required to eliminate the old tutor from the rascal package. They never made it into an IDE like VScode or Eclipse and no stable commandline release was distributed either.

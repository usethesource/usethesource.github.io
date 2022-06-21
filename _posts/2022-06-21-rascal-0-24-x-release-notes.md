---
layout: post 
published: true
author: "Jurgen J. Vinju"
authorlink: "http://www.rascal-mpl.org"
title: "Rascal 0.24.x release notes"
---

In this post we report on the Rascal release 0.24.x

---

## Release 0.24.0 - June 21, 2022

Release 24.x is a maintenance release. A lot of changes happened between 0.17.0 and 0.23.x, so if you have not looked here for a while, go to the [release notes for 0.23.x](https://usethesource.io/rascal-0-23-x-release-notes)

* ParseTree::parser and ParseTree::parsers now generate parsing closures that do not need a JVM lock to synchronize on the Evaluator anymore. 
* Also both functions now capture the generated Class<?> instance instead of a handle to the grammar, for efficiency's sake
* The interpreter's implementation of concrete syntax does not do its own parser caching anymore. Instead it relies on the aforementioned
parsing closures. This saves memory (fewer hash-tables) and also more sharing is possible between parsers for different modules that happen to have the same grammar.
* Issue #1615 was solved
* Issue #1614 was solved
* Issue #1613 was solved by providing `loc` based interfaces to files and programs passed to util::ShellExec. The old `str` based interfaces are now deprecated.

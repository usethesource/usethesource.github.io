---
layout: post 
published: true
author: "Jurgen J. Vinju and Paul Klint"
authorlink: "http://www.rascal-mpl.org"
title: "Rascal 0.17.x release notes"
---

In this post we report on the Rascal release 0.17.x, which includes all changes since the 0.16.x releases. 

---

## Release 0.17.0 - March 16th, 2020

The 0.15.x releases served as daily pre-releases for 0.17.0, while 0.16.x was a stable release which included all patches since 0.10.0. The releases between 0.10.0 and 0.16.0 have mainly been concerned with bootstrapping and minor bugfixes.

The current release 0.17.x is a step towards bootstrapping the Rascal compiler and making the new static checker (type checker) available. 

The static checker:

* checks all features of Rascal
* is written in Rascal using the [TypePal framework](https://github.com/usethesource/typepal)
* is activated on "project clean" and "file save"
* runs for now in the Rascal interpreter and may be slow on bigger projects (this is transitional, so bear with us)
* enables editor features such as hover-help and jump-to-definition in Eclipse, based on the state of the file after the last "save"
* using the Eclipse Preferences: Eclipse > Preferences > Rascal > Enable Rascal Compiler, type checking can be turned on or off

Also in this release significant steps have been made towards Rascal project deployment:

* In RASCAL.MF, Use `Required-Libraries: |lib://myDependency|` to declare projects you depend on
* Declare a project using `Project-Name: projectName` in RASCAL.MF
* The `|lib://name|` scheme always resolves to the root of a jar or target folder for a project with that name
* Eclipse, maven and Junit use the above information to configure interpreter and compiler search paths correctly
* The starting point is the JVM classpath: every RASCAL.MF file found on this path leads to a loadable library
* IDEs such as Eclipse dynamically resolve `lib://` references to respective project's target folders if so required

Other notable changes:

* all static errors and warnings in the standard library have been resolved
* general code cleanup
* resolved many issues (thanks all for reporting!)
* various performance improvements


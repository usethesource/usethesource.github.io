---
layout: post 
published: true
author: "Jurgen J. Vinju"
authorlink: "http://www.rascal-mpl.org"
title: "Rascal 0.27.x release notes"
---

In this post we report on the Rascal release 0.27.x

<!--truncate-->

## Release 0.27.2 - November 23, 2022

* the tutor compiler now takes screenshots if an interactive visual is generated in a rascal-shell code block.
* the JSON serializer maps objects to constructors one-to-one now. Only [AlgebraicDataTypes](/docs/rascalopedia/algebraicdatatype/) with single constructors are allowed, or lists of nullary constructors (for enums).
* added vis::Chart with 8 basic chart styles based on chart.js
* added util::Validator which can validate any `node` instances against an [AlgebraicDataType](/docs/rascalopedia/algebraicdatatype/) using matching and memoized backtracking. Useful for reading in complex XML, JSON or YAML data.
* issue with variablescope leakage in the visit statement was fixed.

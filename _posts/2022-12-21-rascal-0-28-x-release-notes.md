---
layout: post 
published: true
author: "Jurgen J. Vinju"
authorlink: "http://www.rascal-mpl.org"
title: "Rascal 0.26.x release notes"
---

In this post we report on the Rascal release 0.28.x

<!--truncate-->

## Release 0.28.1 - December 2022

* vis::Charts, vis::Graphs and vis::Text were added to the standard library for visualizing charts, graphs and pretty textual values.
* for Eclipse, several older issues and newer issues were fixed in the run-time of the Figure library
* in Eclipse and VScode the new logo was applied, as well as on http://www.rascal-mpl.org
* util::Validator was added to the standard library: a generic validation module for loading node values produced by reading in XML, JSON or YAML (for example) as verified constructors of algebraic data-types.
* In lang::json::IO  the writing of Rascal values to JSON streams was simplified and rationalized. Now every constructor application corresponds to one object, and the fields of Rascal constructors and nodes (keyword fields as well as positional) are always mapped one-to-one to JSON fields by name. Mapping back from JSON values to Rascal can be hard if there are more than one constructors for a data type. In this case have a look at util::Validator.
* Most documentation was moved from the rascal project to the rascal-website project; this will make it easier and faster to contribute to (fixes in) the Rascal documentation.
* Rascal-tutor compiler was improved in many dimensions: screenshots of visuals were added and the compiler is incremental now per Markdown/Rascal file.

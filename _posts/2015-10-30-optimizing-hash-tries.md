---
published: true
title: Optimizing Hash Tries
author: Jurgen Vinju
authorlink: "http://homepages.cwi.nl/~jurgenv/"
layout: post
---

Hash-tries are the data-structure under Rascal's sets, maps and relations. These papers explain how they work and how we make them lean and fast on the JVM. [Others](https://blog.acolyer.org/2015/11/27/hamt/) have blogged about these results as well. The code can be found in the [Capsule project](http://www.usethesource.io/projects/capsule).

```
@inproceedings{oopsla2015,
  title = {Optimizing Hash-Array Mapped Tries for Fast and Lean Immutable JVM Collections}
  author = {Michael Steindorder and Jurgen J. Vinju}.
  year = 2015,
  booktitle = {Proceedings of the Annual ACM SIGPLAN Conference on Object-Oriented Programming, Systems, Languages, and Applications (OOPSLA)},
  editor = {Patrick Eugster},
  fulltext = "http://michael.steindorfer.name/publications/oopsla15.pdf",
}

@inproceedings{gpce14,
 author = {Steindorfer, Michael J. and Vinju, Jurgen J.},
 title = {Code Specialization for Memory Efficient Hash Tries},
 booktitle = {Proceedings of the 2014 International Conference on Generative Programming: Concepts and Experiences},
 series = {GPCE 2014},
 year = {2014},
 pages = {11--14},
 numpages = {4},
 doi = {10.1145/2658761.2658763},
 publisher = {ACM},
 fulltext = "http://michael.steindorfer.name/publications/gpce14.pdf"
} 
```

The data structures under-pinning collection API (e.g. lists, sets, maps) in the standard libraries of programming languages are used intensively in many applications. The standard libraries of recent Java Virtual Machine languages, such as Clojure or Scala, contain scalable and well-performing immutable collection data structures that are implemented as Hash-Array Mapped Tries (HAMTs). HAMTs already feature efficient lookup, insert, and delete operations, however due to their tree-based nature their memory footprints and the runtime performance of iteration and equality checking lag behind array-based counterparts. This particularly prohibits their application in programs which process larger data sets. In this paper, we propose changes to the HAMT design that increase the overall performance of immutable sets and maps. The resulting general purpose design increases cache locality and features a canonical representation. It outperforms Scala’s and Clojure’s data structure implementations in terms of memory footprint and runtime efficiency of iteration (1.3– 6.7 x) and equality checking (3–25.4 x).

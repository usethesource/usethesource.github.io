---
published: true
title: Performance Modeling of Maximal Sharing - Experience Report
author: Michael Steindorfer
authorlink: "https://www.cwi.nl/people/2551"
layout: post
---

This paper won a Best Paper award at ICPE 2016 in Delft. 

```
@inproceedings{icpe2016-steindorfer,
 author = {Michael Steindorfer and Jurgen J. Vinju.},
 title = {Performance Modeling of Maximal Sharing},
 booktitle = {7th ACM/SPEC International Conference on Performance Engineering (ICPE)},
 year = 2016,
 fulltext = "http://homepages.cwi.nl/~jurgenv/papers/ICPE16.pdf"
}
```

It is noticeably hard to predict the effect of optimization strategies in Java without implementing them. “Maximal sharing” (a.k.a. “hash-consing”) is one of these strategies that may have great benefit in terms of time and space, or may have detrimental overhead. It all depends on the redundancy of data and the use of equality. We used a combination of new techniques to predict the impact of maximal sharing on existing code: Object Re- dundancy Profiling (ORP) to model the effect on memory when sharing all immutable objects, and Equals-Call Profil- ing (ECP) to reason about how removing redundancy impacts runtime performance. With comparatively low effort, using the MAximal SHaring Oracle (MASHO), a prototype pro- filer based on ORP and ECP, we can uncover optimization opportunities that otherwise would remain hidden. We report on the experience of applying MASHO to real and complex case: we conclude that ORP and ECP combined can accurately predict gains and losses of maximal sharing, and also that (by isolating variables) a cheap predictive model can sometimes provide more accurate information than an expensive experiment can.

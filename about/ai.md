---
title: AI rules
---

The application of AI -in particular Large Language Models (LLMs)- is interesting for 
UseTheSource projects. Although most of the practical consequences are already outlined [elsewhere](/about/index),
we explain some of the consequences here for our contributors. Two different aspects:

1. AI applied to UseTheSource source code itself
2. AI applications of {sofware,natural} language processing

#### AI applied to UseTheSource source code itself: no

When AI is used to _generate_ or _transform_ source code of UseTheSource projects be **aware**
that you might easily be failing compliance with the [Contributor License Agreement](https://github.com/usethesource/usethesource.github.io/blob/master/about/index.md#:~:text=Contributor%20License%20Agreement) that you signed:

> * [x] Each contribution which I submit is and will be an original work of authorship and I can legally contribute it to open-source.
> * [x] To the best of my knowledge each contribution I submit will not violate any copyright laws, trademarks, patents, or other intellectual property rights.

Conclusion: you currently can't use an LLM to literally generate or transform code for our projects.

#### AI applications of {software,natural} language processing: yes, with caution.

As LLM's are (natural) language processors and UseTheSource is all about software language processing, there is opportunity to combine the two. All kinds of experiments regarding the use of LLM's in UseTheSource projects have common issues. At least you as a UseTheSource contributor must:
0. If code **generation** or **transformation** is the topic, see [above](https://usethesource.io/about/ai.html#:~:text=AI%20applied%20to%20UseTheSource%20source%20code%20itself%3A%20no) for issues with licensing and other rights. Be very careful.
1. If **publication** under real person author names, pseudonyms, or avatars, of AI generated language is a feature, then [see above](https://usethesource.io/about/ai.html#:~:text=AI%20applied%20to%20UseTheSource%20source%20code%20itself%3A%20no) for issues with licensing and other rights. Be very careful. Publication types to think about include:
    * scientific pre-prints, conference proceedings and journals;
    * blogs and vlogs
    * natural language and code in messages in issue trackers, or pull requests;
    * answers on stackoverflow.com, discussion sites and other Q/A media;
    * books and chapters of books
1. Manage and communicate usage **licenses** of existing LLMs (open-source or not), and make sure your users are also made aware of their rights and obligations. Especially privacy is an interesting topic to manage, but also code ownership, licenses and other rights
2. Manage and communicate the **environmental impact** of the training and usage of LLMs. And also communicate clearly to users what this impact was/is.
3. Do no harm. Understand and manage the level of **expertise** in the target community for their project. Will the introduction of the LLM increase or decrease the expertise level in this community? Is that really beneficial? 
4. Give the **user agency** over the choice of LLM to use for each task (download and install, or webservice connectivity). Possibly also the users of our users.
   * this means never linking and LLM into a jar, or downloading it just-in-time under-the-hood.
   * this also means users have to provide their own credentials to AI behind web services



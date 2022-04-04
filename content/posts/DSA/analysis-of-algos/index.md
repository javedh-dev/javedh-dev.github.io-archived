---
title: "Analysis of Algorithms"
date: 2022-04-03T11:10:08+05:30
draft: false
latex: true
tags: [dsa, analysis, interview]
categories: DSA
cover:
    image: "aaa.svg"
    alt: "Hero Image"
    caption: "Analysis of algorithms"
    relative: false # To use relative path for cover image, used in hugo Page-bundles
---

Analyzing algorithms is one of the most important tasks while developing and using an algorithm in an application.

Algorithm analysis helps in -

-   Comparing multiple algorithms, which will perform better in given scenario
-   Better performance leads to scalability etc.

One of the way to analyze algorithms is to implement algorithms and execute on machine to analyze which one runs faster. This approach has multiple flaws like -

-   An algorithm might be faster for one kind of inputs but slower for other.
-   An algo can be faster on one kind of machine and vice-versa

That's where concept of asymptotic notation comes into play

**Asymptotic Notation**

In this approach we evaluate the performance of an algorithms in terms of the input size i.e. How the time or space increases with increase in input size

For eg. -

Let's say our algorithm calculates sum of numbers from (1...n) in **x** unit of time. Now when we doubled the number (1...2n) the time taken by our algorithm also doubled **(2x)** and so on... In this case it is safe to say that execution time of the algorithm is linearly dependent on input size.

Now few point to note here -

-   As we are saying execution time in terms of input size so it is not machine dependent, no matter what kind of machine is there the relation hold true.
-   Usually in a specific algorithm most dynamic parameter is it's input size as hardware and other things are rarely going to change.
-   We mostly work with the order of growth. hence constant factor is usually ignored. i.e. If two algorithms take 2n and 2000000n time. these both are asymptotically same as order of growth is **n**
-   Ignoring the constant factor seems like a ridiculous approach from above example but this usually make sense when input size (**n**) is big enough. For eg. $$\lim_{x \to \infty} cx$$ **c** can be ignored as ${x \to \infty}$

Let's see what kind of annotations are available by taking some algorithm examples in next section.

**See you in next post, till then... 👋**

---
date: "2026-05-15"
title: Erasure in Newt
draft: false
---

About a week ago, I replaced the quantity checking and code extraction in Newt with a newly published technique.

## Initial implementation

When I started Newt, I realized that as a dependent typed language, I needed to remove erased terms during code generation (they can slow down the program). I loosely followed Idris did. I have `0` annotations in the surface syntax, and replace erased terms with `null` in the compiled code.

The code to erase values was rather ad-hoc. I walked through the term, keeping track of quantity in an environment, replaced erased values with a placeholder, and threw an error if an erased value was used as an unerased argument. There were a couple of places where it didn't know if an application was erased or not and I simply assumed unerased to error on the side of safety.

The code generation put in `null` for erased values, and later elided erased arguments on top level functions and constructors. But I still needed erased args on the closures and application of erased positions of closures, because I wasn't tracking that information.

As I started thinking about adding a C backend, I realized that I needed to leave the erased positions on the top level functions to make the closures work correctly. Because the applications were still there for erased arguments.

## New Implementation

Around that time, I saw that Constantine Theocharis and Edwin Brady published "[Type Theory with Erasure](https://arxiv.org/abs/2605.00655)". And I liked that approach. It presents erasure as a phase distinction. There is a formal treatment that I skimmed, but to be honest, I need more background to follow some of that. (And I wanted to get on with the implementation.) They also provide a couple of [sample implementations](https://github.com/kontheocharis/erasure-impl) based on elaboration zoo, which were helpful.

The appeal to me was that it checks the erasure during type checking, and it removes erased applications and lambdas during extraction (code generation). That simplifies both my backend implementation and the emitted code.

The process went fairly smoothly. Wire the flag and quantity into the context and the quantity on `App`. As a bonus, I now get quantities when I dump the context. I got the elaboration working and then worked on the back end. One spot I spent a little time debugging was due to bug in the original code. I was passing Nil-like constructors to the code for a Cons-like constructors, and it happened to work anyway in the original code.

## Todo

There are still some checks that I should add to pattern unification, and I'd like to port all of the test cases from the sample implementation.

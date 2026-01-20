---
date: '2025-11-22'
draft: false
title: Advent of Code
---
_This post contains some minor spoilers about Advent of Code problems._

Advent of Code (AoC) is a holiday event that presents programming challenges over the course of 25 days in December. Each day is broken into two parts, where completing the first unlocks the second. The second part tends to be more difficult, and the first few days are usually easier than the rest. The puzzles have a fun, christmas themed story. I prefer this over some of the other programming challenges that if seen because it presents a bit more of a complete problem, where you have to figure out how you're going to approach solving it. I've been using Advent of Code to try out new languages, doing a different language each year. I also set myself the challenge of working without any hints.

## [2019 {{< icon "github" >}}](https://github.com/dunhamsteve/aoc2019)

{{<badge>}}Haskell{{</badge>}}

The first year that I tried AoC was 2019, which I did in Haskell.  I had written some small bits of code in Haskell and read papers on its implementation, but never a "real" program. When I sat down to do the first day's problem, I realized that I didn't even know how to read a file in Haskell.

Fortunately, it starts out slow, which lets me get my bearings in the new language. Threaded through the challenges this year is a little virtual machine that runs "IntCode". You build it out, add more instructions, write code to interact with a machine or have them interact with each other. It culminates with a text adventure that you can solve by hand or write code to solve. I chose to use an `STArray` for the memory, which provided me a crash course on working with monads. I later looked at an experienced Haskell programmer's solutions and was surprised to learn that a simple associative array was fine. I guess the memory wasn't changed that much.

Another problem required A* search, which I hadn't used since college and was excited to get a chance to use again. And one used the chinese remainder theorem, which I did not recall. But I managed to derive it from first principles in this case.

Overall, this was my favorite year, because of the virtual machine problems and also because it was my first year.

## [2020 {{< icon "github" >}}](https://github.com/dunhamsteve/aoc2020)

{{<badge>}}Python{{</badge>}}

In 2020, my kid was looking over my shoulder, and I was in a hurry, so I did it in python. It looks like I did the first few days in Haskell, too.

## [2021 {{< icon "github" >}}](https://github.com/dunhamsteve/aoc2021)

{{<badge>}}Idris{{</badge>}}

This year marked the start of my journey with Idris and dependent type theory. I had come across the language after playing with the code generation of PureScript.  I wanted to know how avoided fully currying functions. The community was welcoming and I was fascinated by the Curry-Howard correspondence and dependent type theory. I did Advent of Code in Idris to help learn the language and started contributing to it after that. It was fun to help out, and I wanted to learn how it worked.

## [2022 {{< icon "github" >}}](https://github.com/dunhamsteve/aoc2022)
{{<badge>}}Lean4{{</badge>}}

In 2022, I intended to do Advent of Code in Rust. I wanted experience with the novel memory management system. But simultaneously I had been taking a look at Lean and a post on Zulip inspired me to give it a try for Advent of Code. So I redid the first few in Lean4, then started doing Lean4 first. And after a dozen days, it was enough work that I didn't bother reworking the solutions in rust. 

## [2023 {{< icon "github" >}}](https://github.com/dunhamsteve/aoc2023)

{{<badge>}}Lean4{{</badge>}}

I intended to take a look at OCaml for 2023, but I ended up doing Lean4 again because it was more fun.

## [2024 {{< icon "github" >}}](https://github.com/dunhamsteve/newt/tree/main/aoc2024)

{{<badge>}}Newt{{</badge>}}

2024 was a milestone for me. I completed Advent of Code in my own language, Newt. I had just gotten Newt into a state where this was possible at the end of November. Along the way I fixed a few bugs and enhanced the language. My ordered map didn't have a `delete` function at the beginning, and there was a bug to fix before I could make it typecheck, but I had thought to do this a few days before I needed it.

## [2025 {{< icon "github" >}}](https://github.com/dunhamsteve/newt/tree/main/aoc2025)

{{<badge>}}Newt{{</badge>}}

Starting in 2025, Advent of code only runs for twelve days. I'm getting to the point where it is a bit played out, and I have other things that I want to do, so I was happy to see this. I did it in Newt again, and things went fairly well aside from Day 10. I mainly tried a linear algebra solution to solve the diophantine equations, spent a lot of time trying stuff, occasionally trying an alternative, search-based solution. I eventually cut and used Z3 which contains a diophantine equation solver. It feels like cheating, but it did take a little effort to build a library around the node module, wrapping javascript async in a monad. I did this, finished day 12.

I think I know what I was getting wrong on the other solution. I needed to work with a different matrix. But I needed a break, so I'll finish that off later. I did add `Vect` and `Fin` to the library and fixed a few bugs in Newt, so the effort with the matricies was worth it regardless. I won't look at other solutions until I go back and make that work.


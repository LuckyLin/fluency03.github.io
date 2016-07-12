---
title: 'Scala Study Note 3: Scala Scripts | Scala 学习笔记 (三): Scala 脚本'
layout: post
date: '2016-07-11 22:25'
tag:
  - Scala
  - Programming
  - Programming Language
  - Functional Programming
  - Object-oriented Programming
blog: true
---

*Please find all blog posts in the index page: [Index: Scala Study Note \| 目录: Scala 学习笔记](https://fluency03.github.io/scala-study-note-index/)*

---

<div class="breaker"></div>


# Scala Scripts

In this post, several Scala expressions/syntax/grammers are illustrated using Scala scripts.


## Control Constructs

The control constructs in Scala are: *if-statement*, *for-loop*, *while-loop* and *do-while-loop*.



### if-statement

The if-statement is commonly existing in most of the programming languages for conditional branches. Particularly, in Scala, if-statements are expressions meaning that they can return a (single) value.

<script src="https://gist.github.com/fluency03/de4a7c0d9aa368263feb1a077cbcad2c.js"></script>

Technically, the curly braces "\{" and "\}" can be omitted, if the code consists of a single line in the conditional branch body. However, according to [Scala Style Guide: Curly Braces](https://github.com/databricks/scala-style-guide#curly-braces), the following statements are made:

> *Put curly braces even around one-line conditional or loop statements.*

There is an exception, like the Line 28 in above code snippet.

> *The only exception is if you are using if/else as an one-line ternary operator that is also side-effect free.*










### for-loop








### while-loop








### do-while-loop
















---

In the next post - [Scala Study Note 4: First Scala Programs \| Scala 学习笔记 (四): 第一个 Scala 程序](https://fluency03.github.io/scala-study-note-4/), you will write the first Scala program.


<div class="breaker"></div>



## References


* [1] [Odersky, Martin, Lex Spoon, and Bill Venners. *Programming in scala*. Artima Inc, 2008.][1]
* [2] [Scalacheat, Scala Official Documents. ][2]



[1]: https://cs.uwaterloo.ca/~brecht/courses/702/Possible-Readings/scala/ProgrammingInScala.pdf
[2]: http://docs.scala-lang.org/cheatsheets/

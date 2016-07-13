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

The for-loop in Scala is very tricky and is having more functionalities than a Java's for-loop. The following code snippet (from [[2]]) is demonstrating most of the for-loop cases in Scala. In the demonstration, the usage of `yield`, `filter`, `map`, `zip` and `flatMap` will be explained in the following posts.

<script src="https://gist.github.com/fluency03/2c41628df42164ccd8ea324c39a3e469.js"></script>


 - `for (x <- xs if x % 2 == 0)`. The array `xs` is iterated using the generator notation ( `<-` ). For each iteration the next element in the array is assigned to the val `x` under the given condition. This condition, or so-called filter as given in the code `if x % 2 == 0`, means that the for-loop only executes its body if the assigned value to `x` from `xs` is even.
 - `((x,y) <- xs.zip(ys))`. The two arrays `xs` and `ys` can be coupled together in order to form an array of tuples. The new array is with length of the minimium length between `xs` and `ys`.
 - `(x <- xs; y <- ys)`. In Scala, it is possible to implement a nested loop in a single for-loop. The iteration `x <- xs` is the outer loop, and the `y <- ys` is the inner loop.
 - `(i <- 1 to 5)` vs. `(i <- 1 until 5)`. You can use either the keyword `to` or `until` when creating a `Range` object. The difference is, that `to` includes the last value in the range, whereas `until` leaves it out. The first loop iterates 5 times, from 1 to 5 including 10. The second loop iterates 4 times, from 1 to 4, excluding the upper boundary value 10.


Using the `yield` keyword, we can apply the *for expressions* to create new collections.

Another implement of for expression is the `foreach` method of collections such as:
{% highlight scala %}
val ys: Array[Int] = Array(1, 2, 3, 4, 5)
ys.foreach(println)
{% endhighlight %}

It will print each of the elements of array `ys` as following:
{% highlight raw %}
1
2
3
4
5
{% endhighlight %}




### (do-)while-loop

The while-loop in Scala has nothing special.

<script src="https://gist.github.com/fluency03/bebb6b5fee1a9aeb1d6f204a5ee68574.js"></script>






## Arrays and Lists



















## Tuples


















## Sets and Maps















## Functional Style




















## Read Files
















---

In the next post - [Scala Study Note 4: First Scala Programs \| Scala 学习笔记 (四): 第一个 Scala 程序](https://fluency03.github.io/scala-study-note-4/), you will write the first Scala program.


<div class="breaker"></div>



## References


* [1] [Odersky, Martin, Lex Spoon, and Bill Venners. *Programming in scala*. Artima Inc, 2008.][1]
* [2] [Scalacheat, Scala Official Documents. ][2]



[1]: https://cs.uwaterloo.ca/~brecht/courses/702/Possible-Readings/scala/ProgrammingInScala.pdf
[2]: http://docs.scala-lang.org/cheatsheets/

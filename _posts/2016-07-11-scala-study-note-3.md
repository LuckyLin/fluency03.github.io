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

The key words `to` and `until` can also be applied as following:
{% highlight scala %}
for (i <- 1.to(5)) {
// or, for (i <- 1 to 5) {
  println(i)
}

for (i <- 1.to(5).by(2)) {
// or, for (i <- 1 to 5 by 2) {
  println(i)
}

for (i <- 1.until(5)) {
// or, for (i <- 1 until 5) {
  println(i)
}

for (i <- 1.until(5).by(2)) {
// or, for (i <- 1 until 5 by 2) {
  println(i)
}
{% endhighlight %}

When `1 to 5` is typed into the Scala interpreter, the method named `to` is actually invoked on the `Int` object `1`. Then the `5` is passing as a parameter of method `to`. Therefore, the expression `1 to 5` can be alternatively written as typical method invocation syntax: `(1).to(2)`. Same case is applied on `until` as well. Additionally, you can also apply `by` in order to indicate the step.

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






## Arrays



In Scala, the objects or class instances can be instantiated using the keyword `new`. In the following example, two ways of declaring an array are demonstrated.

{% highlight scala %}
val stringArray1 = new Array[String](3)
// or more explicitly, val stringArray1: Array[String] = new Array[String](3)

stringArray1.update(0, "zero")
stringArray1.update(1, "one")
stringArray1.update(2, "two")
// same as
stringArray1(0) =  "zero"
stringArray1(1) = "one"
stringArray1(2) = "two"


val stringArray2 = Array("zero", "one", "two")
{% endhighlight %}

In this example, `stringArray1` is a value of type `Array[String]` (an "array of string") that is initialized to length 3 by parameterizing it with the value 3 in the first line of code.
This instance `stringArray1` is parameterized with both a type (`String`) and a value (`3`). The type comes first in its square brackets, indicating the type of elements in the array, which is followed by the value in parentheses, indicating the length of the array. The method `update` called by `stringArray1` takes two parameters: (i) an interger as the position index on the array; (ii) a string that will be filling the exact position on the array. Another way of updating the string array is directly accessing by placing the index inside parentheses and using equals sign.
Unlike the array access in Java, where square brackets are used to keep the index, parentheses are used in Scala.


Additionally, you can also directly initialize the array at the first time when it is defined and declared as `val stringArray2 = Array("zero", "one", "two")`, which is more concise. The compiler will automatically infer the type of the array's elements to be `String` since strings are passed into it.


According to [[1]], "*Scala achieves a conceptual simplicity by treating everything, from arrays to expressions, as objects with methods. You don't have to remember special cases, such as the differences in Java between primitive and their corresponding wrapper types, or between arrays and regular objects. Moreover, this uniformity does not incur a significant performance cost. The Scala compiler uses Java arrays, primitive types, and native arithmetic where possible in the compiled code.*"





## Lists




{% highlight scala %}

{% endhighlight %}














## Tuples





{% highlight scala %}

{% endhighlight %}












## Sets and Maps




{% highlight scala %}

{% endhighlight %}










## Functional Style



{% highlight scala %}

{% endhighlight %}
















## Read Files



{% highlight scala %}

{% endhighlight %}












---

In the next post - [Scala Study Note 4: First Scala Programs \| Scala 学习笔记 (四): 第一个 Scala 程序](https://fluency03.github.io/scala-study-note-4/), you will write the first Scala program.


<div class="breaker"></div>



## References


* [1] [Odersky, Martin, Lex Spoon, and Bill Venners. *Programming in scala*. Artima Inc, 2008.][1]
* [2] [Scalacheat, Scala Official Documents. ][2]



[1]: https://cs.uwaterloo.ca/~brecht/courses/702/Possible-Readings/scala/ProgrammingInScala.pdf
[2]: http://docs.scala-lang.org/cheatsheets/

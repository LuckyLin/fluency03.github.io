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

<!-- One of the big ideas of the functional style of programming is that methods should not have side effects. A method's only act should be to compute and return a value. Some benefits gained when you take this approach are that methods become less entangled, and therefore more reliable and reusable. Another benefit (in a statically typed language) is that everything that goes into and out of a method is checked by a type checker, so logic errors are more likely to manifest themselves as type errors. Applying this functional philosophy to the world of objects means making objects immutable. -->

In Scala, the `Array` is a mutable sequence of objects that all share the same type. After an array is instantiated, the length of the array cannot be changed whereas the element values are changable.

Different from the `Array`, the `List` in Scala are always immutable, which means that a Scala `List` can’t be modified once created, (which is also different from the lists in Java). Such lists are designed to enable a functional style programming sicne *one of the big ideas of the functional style of programming is that methods should not have side effects* [[1]]. So how operators are invoked on Scala `List` if they are immutable? When any operation is invoked on a `List`, another `List` is created and returned when an operator is applied. Even though a list is not appendable, it is prependable, since prepending an element at the beginning of a list is in constant-time, whereas appending is a linear-time operation frowing with the size of the list.


The two main operators for `List` are `:::` and `::`. The first one is the operator for list concatenation. The second one is the operator to prepend an element to a `List`. Normally, the owner of an operation is the left operand, but the moethod `::` is of the right operand.


{% highlight scala %}
val list1 = List(1, 2)
val list2 = List(3, 4)
val list3 = list1 ::: list2
val list4 = 5 :: list3
println(list1)
println(list2)
println(list3)
println(list4)

/**
 * List(1, 2)
 * List(3, 4)
 * List(1, 2, 3, 4)
 * List(5, 1, 2, 3, 4)
 */
{% endhighlight %}


<!-- List1 and list2 remain immutable, they didn’t change. List3 is a new list resulting of concatenating list1 and list2. In list4, the String “Hey!” is prepended to list3. -->




## Tuples

Like lists, tuples are immutable, but unlike lists, tuples can contain different types of elements. Tuples are very useful, for example, if you need to return multiple objects from a method. Once a tuple has been instantiated, its elements can be accessed directly and individually with a *dot*, *underscore*, and the one-based index of the element, i.e., 1 and 2 if the tuple is having two elements. An example is shown in the following:

{% highlight scala %}
val pair = ("Chang Liu", 1991)
println(pair._1)
println(pair._2)

/**
 * Chang Liu
 * 1991
 */
{% endhighlight %}


The tuple `pair` in the code snippet is referred to be the type of `Tuple2[String, Int]`. Additionally, the type of the tuple `("Chang Liu", 1991, "May", 2, "China", "Male")` is `Tuple6[String, Int, String, Int, String, String]`.


<!-- You may be wondering why you can't access the elements of a tuple like the elements of a list, for example, with "pair(0)". The reason is that a list's apply method always returns the same type, but each element of a tuple may be a different type: _1 can have one result type, _2 another, and so on. These _N numbers are one-based, instead of zero-based, because starting with 1 is a tradition set by other languages with statically typed tuples, such as Haskell and ML. -->








## Sets


There are two kinds of `Set`, the immutable and the mutable one， where the difference is that when an object is immutable, the object itself can’t be changed, just like `String` in Java. By default, Scala uses the immutable `Set`. If you want to use the mutable `Set`, you’ll have to import the class specifically by `import scala.collection.mutable.Set`. The hierarchy of the `Set` is shown in the following:

{% highlight scala %}
                                          |----------------------|
                                          |      <<trait>>       |
                                          | scala.collection.Set |
                                          |----------------------|
                                                     |
                                                     |
                   |----------------------------------------------------------------------|
                   |                                                                      |
                   |                                                                      |
  |--------------------------------|                                       |------------------------------|
  |            <<trait>>           |                                       |           <<trait>>          |
  | scala.collection.immutable.Set |                                       | scala.collection.mutable.Set |
  |--------------------------------|                                       |------------------------------|
                   |                                                                       |
                   |                                                                       |
                   |                                                                       |
|------------------------------------|                                   |----------------------------------|
| scala.collection.immutable.HashSet |                                   | scala.collection.mutable.HashSet |
|------------------------------------|                                   |----------------------------------|
{% endhighlight %}



As you can see, there is a base `trait` for sets, i.e. `scala.collection.Set`, where a trait is similar to a Java interface. Scala then provides two subtraits, one for mutable sets and another for immutable sets. These three traits, with different full name, all share the same simple name, i.e., `Set`. A concrete set class in the Scala API extend either the mutable or immutable `Set` trait. (Although in Java you "implement" interfaces, in Scala you "extend" or "mix in" traits.) Thus, if you want to use a `HashSet`, you can choose between mutable and immutable varieties depending upon your needs in order to take advantage of both functional and imperative styles.



{% highlight scala %}
var numSet = Set("zero", "one", "two")
numSet += "three"
println(numSet)
/** Set(zero, one, two, three) */
{% endhighlight %}



An immutable set can be defined as a new `var`, as the `numSet` shown above, and meanwhile, initialized with three elements (Strings): "*zero*", "*one*", and "*two*".
The Scala compiler will infer `numSet`'s type to be the immutable `Set[String]`.

The method `+` can be called on the set in order to add a new element. Both mutable and immutable sets offer a `+` method but with different behaviors. Whereas a mutable set will add the element to itself, an immutable set will create and return a new set with the element added. Such behavior makes the immutable set immutable and reduces the side effects of methods.
Although mutable sets offer an actual += method, immutable sets do not.


{% highlight scala %}
import scala.collection.mutable.Set

val alphaSet = Set("a", "b", "c")
alphaSet += "d"
/**
 * same as:
 * alphaSet.+=("d")
 */
println(alphaSet)
/** Set(c, d, a, b) */
{% endhighlight %}


Like Java, you can import a Scala API by giving its fully qualified name so that a simple name, such as `Set`, instead of the longer name, can be applied every time you want to use it. Then, when you say `Set`, the compiler will know that it refers to `scala.collection.mutable.Set` as you imported. In above code snippet, the mutable set `alphaSet` isinitialized with alphabet strings "*a*", "*b*" and "*c*". Then the string "*d*" is added to the mutable set by calling the `+=` method on the set, passing in the string "*d*".

You can also import and use the `HashSet` explicitly as following:

{% highlight scala %}
import scala.collection.immutable.HashSet

val hashSet = HashSet("scala", "java")
println(hashSet + "python")
/** Set(java, scala, python) */
{% endhighlight %}




## Maps

Similarly, `Map` in Scala also follows the same hierarchy.

{% highlight scala %}
                                          |----------------------|
                                          |      <<trait>>       |
                                          | scala.collection.Map |
                                          |----------------------|
                                                     |
                                                     |
                   |----------------------------------------------------------------------|
                   |                                                                      |
                   |                                                                      |
  |--------------------------------|                                       |------------------------------|
  |            <<trait>>           |                                       |           <<trait>>          |
  | scala.collection.immutable.Map |                                       | scala.collection.mutable.Map |
  |--------------------------------|                                       |------------------------------|
                   |                                                                       |
                   |                                                                       |
                   |                                                                       |
|------------------------------------|                                   |----------------------------------|
| scala.collection.immutable.HashMap |                                   | scala.collection.mutable.HashMap |
|------------------------------------|                                   |----------------------------------|
{% endhighlight %}


A mutable `Map` can be imported, defined and initialized as following:

{% highlight scala %}
import scala.collection.mutable.Map

val numMap = Map[Int, String]()
numMap += (1 -> "one")
/**
 * same as:
 * numMap.+= (1 -> "one")
 * or,
 * numMap += (1.->("one"))
 * or,
 * numMap.+=(1.->("one"))
 */
numMap += (2 -> "two")
numMap += (3 -> "three")
println(numMap(1))
/** one */
{% endhighlight %}

The `numMap`, originally, an empty mutable `Map` that has integer keys and string values, without any initial data passed to the factory method. The key/value pairs are passed to the map using methods `->` and `+=`. Similar to the method `+=` as illustrated before, the method `->` is explained in a same way by the Scala compiler, i.e., the binary operation expression `1 -> "one"` is as same as `(1).->("one")`. It is actually a method named `->` called on an integer with the value 1, passing in a string with the value "*one*" This `->` method, which you can invoke on any object in a Scala program, returns a two-element tuple containing the key and value. You then pass this tuple to the `+=` method of the map object to which `numMap` refers.

If you prefer an immutable map, no import is necessary, as immutable is the default map. An example is shown as following:

{% highlight scala %}
val romanNum = Map(
  1 -> "I", 2 -> "II", 3 -> "III", 4 -> "IV", 5 -> "V"
)
println(romanNum(4))
/** IV */
{% endhighlight %}


Given there are no imports, when you say `Map`, you'll get the default: a `scala.collection.immutable.Map`. You pass five key/value tuples to the map's factory method, which returns an immutable `Map` containing the passed key/value pairs.












## Functional Style

When I started to study Scala, such a functional programming language was very new to me and it was very hard to me, who has been programming using Java and C/C++ for a long time. Even now, I am still not completely clear about the functional style. I have been trying very hard to grasp the core ideas behind it, which, of course, will require me to make lots of efforts on looking through various materials and asking many questions. I believe that learning to program in a functional style will not only make me a better Scala programmer but also expand my horizons and make me a better programmer in general. Even though imperative style is allowed in Scala, more functional style is definitely encouraged.


<!-- The first step is to recognize the difference between the two styles in code. One telltale sign is that if code contains any vars, it is probably in an imperative style. If the code contains no vars at all — i.e., it contains only vals — it is probably in a functional style. One way to move towards a functional style, therefore, is to try to program without vars. -->


<!-- The Scala perspective, however, is that val and var are just two different tools in your toolbox, both useful, neither inherently evil. Scala encourages you to lean towards vals, but ultimately reach for the best tool given the job at hand. Even if you agree with this balanced philosophy, however, you may still find it challenging at first to figure out how to get rid of vars in your code. -->

*Programming in Scala* [[1]] is a very good book for learning Scala and obtaining a deeper understanding of functional programming in general.



{% highlight scala %}

{% endhighlight %}















#### A balanced attitude for Scala programmers [[1]]

> *Prefer vals, immutable objects, and methods without side effects. Reach for them first. Use vars, mutable objects, and methods with side effects when you have a specific need and justification for them.*







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

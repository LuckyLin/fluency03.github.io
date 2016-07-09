---
title: 'Scala Study Note 1. | Scala 学习笔记 (一)'
layout: post
date: '2016-06-20 22:25'
tag:
  - Scala
  - Programming
  - Programming Language
  - Functional Programming
  - Object-oriented Programming
blog: true
---

I started to study Scala recently since I found that it is a quite interesting programming language to learn, which is different from other languages I have learned before, such as C/C++, Python and Java. There are many interesting feautures of Scala that I haven't known and the idea of Functional Programming also intrigues me. Therefore, I would like to write a series of blogs recording the process of my study. It will be about the knowledege and practices of Scala. I will also try my best to give my ideas and understanding. This is not only the study notes for keping myself motivated and but also a place where I would like to hear your ideas and thoughts. Please feel free to leave any comments below. To the best of my knowledege, I will answer your questions as possible as I can but be more eager to see you pointing out my mistakes and offering different opinions.

I would first recommend several great Scala materials, which I will mainly rely on during my study.

 - [Scala School](http://twitter.github.io/scala_school/index.html) ([中文版](http://twitter.github.io/scala_school/zh_cn/index.html))
 - [Effective Scala](http://twitter.github.io/effectivescala/) ([中文版](http://twitter.github.io/effectivescala/index-cn.html))
 - [Scala Official Documentations](http://docs.scala-lang.org/index.html)
 - [Programming in Scala, 3ed Edition](http://www.artima.com/shop/programming_in_scala_3ed)

Before start introducing the syntex and grammer of Scala, there are several important notions worth illustrating, with regard of functional programming and object-oriented programming. A clear awareness of these ideas will form a good understanding of the fundimental principles of Scala. In this and the following blogs, it is assumed that the audiences have basic understanding of object-oriented programming and have already possessed the knowledege and experience of at least one of these related languages, such as Java, Python or C++.


## What is Scala?

Scala is a general purpose programming language standing for ''*scalable language*'', principally targeting the Java Virtual Machine (JVM) and interoperating seamlessly with all Java libraries. It is not only a good language for writing scripts but also owning the strengths used for building large systems and software frameworks. A good example of Scala's system framework application is [Apache Spark](http://spark.apache.org/). Designed to express common programming patterns in a concise, elegant, and type-safe way, Scala fuses both [imperative programming](https://en.wikipedia.org/wiki/Imperative_programming) and [functional programming](https://en.wikipedia.org/wiki/Functional_programming) styles.


## Scala is object-oriented

Scala is an object-oriented language in pure form:

 - **Every value is an object.** A contrast example is that, in Java, the primitive values are not objects. Unlike Java, all values in Scala are objects (including numerical values and functions). Since Scala is class-based, all values are instances of a class. The type hierarchy of Scala is illustrated in the following diagram.

 ![Markdowm Image][5]
 <figcaption class="caption">
  Scala Type Hierarchy (Source: [2]).
 </figcaption>

  The `scala.Any` is the most superclass of all classes in Scala. As shown in above figure, it has two direct subclasses - `scala.AnyVal` and `scala.AnyRef` - each of them representing a class world: value classes and reference classes, respectively. The value classes are predefined corresponding to the primitive types (i.e., non-object types) of Java or similar languages. The reference classes are user-defined classes, which are always (directly or indirectly) the subclasses of `scala.AnyRef`. Every user-defined class in Scala implicitly extends the trait `scala.ScalaObject` (the concept of *trait* will be studied later). Classes from the infrastructure on which Scala is running (e.g. JVM) do not extend `scala.ScalaObject`. The `scala.AnyRef` is equivalent to `java.lang.Object`, if Scala is running on JVM. This type hierarchy of Scala will be explicitely explained in the following blogs by having actual code.
  <!-- Please note that the diagram above also shows implicit conversions between the value classes. -->
  <!-- Here is an example that demonstrates that both numbers, characters, boolean values, and functions are objects just like every other object: -->

 - **Every operation is a method call.** A contrast example is that, in Java, it allows static fields and methods that are not members of any object. These ideas might look irrelevant considering it might increase certain language's capability, but they are really annoying when things start to become very complicated and limit the scalability of the program.

 - **Scala is more advanced than most other languages when it comes to composing objects.** "*Types and behavior of objects are described by [classes](http://docs.scala-lang.org/tutorials/tour/classes.html) and [traits](http://docs.scala-lang.org/tutorials/tour/traits.html). Classes are extended by subclassing and a flexible [mixin-based composition](http://docs.scala-lang.org/tutorials/tour/mixin-class-composition.html) mechanism as a clean replacement for multiple inheritance. [[3]]"*
 <!-- Mixin composition takes the members of a class and adds the members of a number of traits to them. In this way, different aspects of classes can be encapsulated in different traits. This looks a bit like multiple inheritance, but differs when it comes to the details. Unlike a class, a trait can add some new functionality to an unspecified superclass. This makes traits more "pluggable" than classes. In particular, it avoids the classical "diamond inheritance" problems of multiple inheritance, which arise when the same class is inherited via several different paths. -->



<!-- For example, when you say 1 + 2 in Scala, you are actually invoking a method named + defined in class Int. You can define methods with operator-like names that clients of your API can then use in operator notation. -->
<!-- This is how the designer of Scala's actors API enabled you to use expressions such as requester ! sum shown in the previous example: '!' is a method of the Actor class. -->




## Scala is functional

The foundation of functional language was laid in Alonzo Church's concept of <span class="evidence">*[lambda calculus](https://en.wikipedia.org/wiki/Lambda_calculus)*</span>, which is a mathematical system consisting of a single transformation rule (variable substitution) and a single function definition scheme. It is a universal computation model that can be used to simulate any single-taped Turing machine, which means Lambda calculus is *[Turing complete](https://en.wikipedia.org/wiki/Turing_completeness)* [[1]].

Functional programming is guided by two main ideas.

<!------------------------------------------------>

#### First-class Functions.

In a functional language, a function is treated as first-class citizen, i.e., a value of the same status such as an integer or a string. That means functions can be passed as arguments to other functions, returned as results from functions, assigned to variables or stored in data structures. Function can also be defined inside another function (i.e., [nested function](https://en.wikipedia.org/wiki/Nested_function)), just like integer values inside a function, or they can be defined without giving them a name (i.e., [anonymous function](https://en.wikipedia.org/wiki/Anonymous_function)).

[Higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) is a very common practice in the programming languages regarding functions as the first-class citizens. It either takes one or more functions as arguments or returns a function as its result. The `map` function is a very well-known example of as a higher-order function which can be found in many languages. It takes, as arguments, a function *f* and a list of elements, and as the result, returns a new element list with *f* applied to each element from the input list. The function *f* performs like a filter.

Functions that are first-class values provide a convenient means for abstracting over operations and creating new control structures [[4]]. This generalization of functions provides great power of expressiveness, which often leads to very legible and concise programs, and also brings a high scalability [[4]].
<!-- As an example, the receive construct shown previously in the actor example is an invocation of a method that takes a function as argument. The code inside the receive construct is a function that is passed unexecuted into the receive method. -->

In Scala, functions are just treated like ordinary variables but with a function type, i.e., every function is a value.


<!-- In most traditional languages, by contrast, functions are not values. Languages that do have function values often relegate them to second-class status. For example, the function pointers of C and C++ do not have the same status as non-functional values in those languages: function pointers can only refer to global functions, they do not allow you to define first-class nested functions that refer to some values in their environment. Nor do they allow you to define unnamed function literals. -->


<!------------------------------------------------>

#### Pure functions.

The operations of a program should only map input values to output values rather than change data in place. Immutable data structures, such as String in Java, are one of the cornerstones of functional programming. The Scala libraries define many more immutable data types on top of those ones defined in Java. For instance, Scala has immutable lists, tuples, maps, and sets.

It can be stated in a different way: methods should not have any side effects. They should communicate with their environment only by taking arguments and returning results, without affecting the program's semantics.

Functional languages encourage *[immutable data](https://en.wikipedia.org/wiki/Immutable_object) structures* and *[referentially transparent](https://en.wikipedia.org/wiki/Referential_transparency) methods*. Some functional languages even require them. Scala offers this as optional. When you want to write the code in an imperative style, mutable data and side effects are available and can be called. However, Scala, as a more functional style language, generally makes it easy to avoid imperative constructs due to the existing good functional alternatives.

Please refer to Wikipedia [Purely Functional](https://en.wikipedia.org/wiki/Purely_functional).


Other features of Scala as a functional language are:

- Currying
- Cloure
- etc.




## Compile and Execute

The way of compiling and executing scala files is as same and easy as how it is done in Java.

The [`scalac`](http://www.scala-lang.org/old/sites/default/files/linuxsoft_archives/docu/files/tools/scala.html) command compiles the Scala source file(s) and generates corresponding Java bytecode which can be executed on any standard JVM. The Scala compiler works similarly to `javac`, which is the Java compiler of the Java SDK.

{% highlight scala %}
> scalac HelloWorld.scala
{% endhighlight %}

The [`scala`](http://www.scala-lang.org/old/sites/default/files/linuxsoft_archives/docu/files/tools/scala.html) command executes the above generated bytecode with certain appropriate options.

{% highlight scala %}
> scala HelloWorld
{% endhighlight %}






## References

* [1] [Turing, Alan M. "Computability and λ-definability." *The Journal of Symbolic Logic* 2, no. 4 (1937): 153-163.][1]
* [2] [Unified Types, Scala Official Documents.][2]
* [3] [Tour of Scala, Scala Official Documents.][3]
* [4] [Odersky, Martin, Lex Spoon, and Bill Venners. *Programming in scala*. Artima Inc, 2008.][4]




[1]: http://www.jstor.org/stable/pdf/2268280.pdf?_=1467991877981
[2]: http://docs.scala-lang.org/tutorials/tour/unified-types.html
[3]: http://docs.scala-lang.org/tutorials/tour/tour-of-scala
[4]: https://cs.uwaterloo.ca/~brecht/courses/702/Possible-Readings/scala/ProgrammingInScala.pdf
[5]: http://lmazy.verrech.net/wp-content/uploads/2011/02/scala_type_hierarchy.png

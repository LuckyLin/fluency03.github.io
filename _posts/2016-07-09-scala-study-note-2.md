---
title: 'Scala Study Note 2: Get Started! | Scala 学习笔记 (二): 上手!'
layout: post
date: '2016-07-09 22:25'
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

The Scala package can be found here: [http://www.scala-lang.org/download/](http://www.scala-lang.org/download/), together with the instructions of installation and configuration. The relevant details will not be given in this post.



You can either use the Scala's interpreter, an interactive shell for writing Scala expressions and programs, or create a file with type of `.scala` just like `.java` in Java. Please refer to the Section [Compile and Execute](#compile-and-execute) in order to get the way of compiling and executing the scala programs.


<div class="breaker"></div>


# Interactive Interpreter

In this part, I will use the interactive interpreter. The interactive interpreter of Scala is an easy way of starting your first line of code. Any Scala expression can be just typed into the interpreter. The code will be interpreted and evaluated, and the result will be printed out on the console. In order to do so, you can simply type the command `scala` at a command prompt as following:

{% highlight scala %}
cliu@cliu-ubuntu:Scala$ scala
Welcome to Scala version 2.11.7 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_74).
Type in expressions to have them evaluated.
Type :help for more information.

scala>
{% endhighlight %}

As you can see, the Scala version I am using is 2.11.7, based on 64-bit Java 1.8.0_74.


## First line of code

For calculating the addition of integers 1 and 2, just type `1 + 2` in the shell and press `Enter`, the result is shown as following:

{% highlight scala %}
scala> 1 + 2
res0: Int = 3
{% endhighlight %}


As to the resulted line `res0: Int = 3`:

  - `res0` --- an automatically generated or user-defined name to refer to the computed value. In this case, it is assigned automatically. `res0` means result 0. The identifier `resX` refers to the Xth result;
  - `:` --- a colon, as "*is of type*", followed by the result type and value;
  - `Int` --- the type of expression;
  - `=` --- an "*equals*" sign;
  - `3` --- the value resulting from evaluating the expression.

Since `res0` was set to 3 previously, `res0 + 3` will be 6 as shown in the following:

{% highlight scala %}
scala> res0 + 3
res1: Int = 6
{% endhighlight %}


If you want to directly print something, just use `println` by passing a string to the standard output, which is similar to `System.out.println` in Java. For example:

{% highlight scala %}
scala> println("Hello, World!")
Hello, World!
{% endhighlight %}



Now, if the `res1` is multiplied by 3, the result is printed out as following:

{% highlight scala %}
scala> res1 * 3
res3: Int = 18
{% endhighlight %}



Notice that the generated identifier of new result is `res3` instead of `res2`. In order to inspect this, we print out all `res0` ~ `res3` as following:

{% highlight scala %}
scala> println(s"$res0; $res1; $res2; $res3")
3; 6; (); 18
{% endhighlight %}

The `res2` is `()`, which is kind of `void` type, which is the result of `println("Hello, World!")`.

Now, if you type `res4`, it will show that:

{% highlight scala %}
scala> res4
<console>:11: error: not found: value res4
       res4
       ^
{% endhighlight %}

It means that the variable `res4` does not exist (has not been created yet).



## Variables

There are two kinds of variables in Scala: `val` (值) and `var` (变量). The `val` is similar to a final variable in Java, which, once initialized, can never be reassigned. The `var`, by contrast, is similar to a non-final variable in Java. The var can be reassigned throughout its lifetime.

{% highlight scala %}
scala> val three = 1 + 2
three: Int = 3

scala> three = 4
<console>:11: error: reassignment to val
       three = 4
             ^

scala> var tempThree = 1 + 2
tempThree: Int = 3

scala> tempThree = 4
tempThree: Int = 4
{% endhighlight %}

In the above exmpale, the `val` named `three` is un-reassignable. However, you can assign an another numeric value 4 to the `var` - `tempThree`.



This following statement introduces msg as a name for the string `"Hello, world!"`.

{% highlight scala %}
scala> val msg = "Hello, World!"
msg: String = Hello, World!
{% endhighlight %}


The type of msg is `String`. In Scala running on JVM, there is no difference between `String` and `java.lang.String` because Scala strings are implemented by Java's String class, as stated in the following:

{% highlight scala %}
type String = java.lang.String
{% endhighlight %}

In the definition of a `val`, neither `java.lang.String` nor `String` need to be declared. This is done by the *type inference* in Scala, which is the capability to figure out the type of a variable. In this case, because you initialized `msg` with a string literal, Scala inferred the type of msg to be String. When the Scala interpreter (or compiler) can infer types, it is often best to let it do so rather than fill the code with unnecessary, explicit type annotations.



In case you would like to input some code spaning multiple lines, just keep typing after the first line. If the code is too far to complete, the interpreter will respond with a vertical bar on the next line, meaning that you can continue typing.

{% highlight scala %}
scala> val multiLine =
     |   "This is the next line."
multiLine:  String = This is the next line.
{% endhighlight %}


If you realize you have typed something wrong, but the interpreter is still waiting for more input, you can escape by pressing enter twice:

{% highlight scala %}
scala> val oops =
     |
     |
You typed two blank lines.  Starting a new command.

scala>
{% endhighlight %}



Some quick references of Scala syntactic constructions regarding variables:

{% highlight scala %}
var x = 5	   /* variable */
val x = 5          /* Good, constant */
x=6	           /* BAD, constant */
var x: Double = 5  /* explicit type */
{% endhighlight %}











## Functions

A simple function `addOne`, which adds one on the input, can be defined following:

{% highlight scala %}
scala> def addOne(m: Int): Int = m + 1
addOne: (m: Int)Int

scala> val three = addOne(2)
three: Int = 3
{% endhighlight %}





{% highlight scala %}

{% endhighlight %}



{% highlight scala %}

{% endhighlight %}





















<div class="breaker"></div>


# Scala Files







## Scala Scripts






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


* [1] [Odersky, Martin, Lex Spoon, and Bill Venners. *Programming in scala*. Artima Inc, 2008.][1]
* [2] [Scalacheat, Scala Official Documents. ][2]



[1]: https://cs.uwaterloo.ca/~brecht/courses/702/Possible-Readings/scala/ProgrammingInScala.pdf
[2]: http://docs.scala-lang.org/cheatsheets/

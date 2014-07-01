Chapter 2
======
Ruby.new

Most books on programming languages look about the same. They start with chapters on basic types: integers, strings, and so on. Then they look at expressions, before moving on to ​if​ and ​while​ statements. Then, perhaps around Chapter 7 or 8, they’ll start mentioning classes. We find that somewhat tedious.

大多数讲编程的书看起来差不多。首先从基本的类型讲起：整型，字符串等等，然后开始讲解表达式，if和while控制结构。之后，大概到七八章的时候才开始提及类。我们发现那太无聊了。

Instead, when we designed this book, we had a grand plan (we were younger then). We wanted to document the language from the top down, starting with classes and objects and ending with the nitty-gritty syntax details. It seemed like a good idea at the time. After all, most everything in Ruby is an object, so it made sense to talk about objects first.

相反，当我们可是写这本书的时候，有一个雄心勃勃的计划(那时我们还很年轻)，我们想自顶而下的介绍Ruby语言。从类和对象开始，最后以详细的语法细节结束。这在开始的时候是不错，因为Ruby里几乎都是对象，所以要从对象讲起是不无道理的。

Or so we thought.

Unfortunately, it turns out to be difficult to describe a language that way. If you haven’t covered strings, ​if​ statements, assignments, and other details, it’s difficult to write examples of classes. Throughout our top-down description, we kept coming across low-level details we needed to cover so that the example code would make sense.

我们曾经这么想过。
遗憾的是，自顶向下方式来介绍一门语言是很困难的。如果不介绍字符串(strings),if语言、赋值和其他语法细节，写一个类(class)的事例都很困难。自顶向下的介绍中，为了使示例代码更明白，只能不断提及语言的细节方面。

So, we came up with another grand plan (they don’t call us pragmatic for nothing). We’d still describe Ruby starting at the top. But before we did that, we’d add a short chapter that described all the common language features used in the examples along with the special vocabulary used in Ruby, a kind of mini-tutorial to bootstrap us into the rest of the book. And that mini-tutorial is this chapter.

所以，我们开始了另外一个雄心勃勃的计划(我们被称为实用主义者)。本书依然自顶而下的介绍Ruby，但在开始之前，我们加了一短章节，用Ruby的方式来描述了例子中要用到的所有常见的Ruby语言的特性，就像一本迷你教程那样，把各位引入到这本书的其他部分。

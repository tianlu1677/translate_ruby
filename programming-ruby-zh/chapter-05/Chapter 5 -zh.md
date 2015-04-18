Chapter 5
====
共享功能: 继承、模块和Mixin(Sharing Functionality: Inheritance, Modules, and Mixins)
====
One of the accepted principles of good design is the elimination of unnecessary duplication. We work hard to make sure that each concept in our application is expressed just once in our code.[32]

We’ve already seen how classes help. All the methods in a class are automatically accessible to instances of that class. But there are other, more general types of sharing that we want to do. Maybe we’re dealing with an application that ships goods. Many forms of shipping are available, but all forms share some basic functionality (weight calculation, perhaps). We don’t want to duplicate the code that implements this functionality across the implementation of each shipping type. Or maybe we have a more generic capability that we want to inject into a number of different classes. For example, an online store may need the ability to calculate sales tax for carts, orders, quotes, and so on. Again, we don’t want to duplicate the sales tax code in each of these places.

In this chapter, we’ll look at two different (but related) mechanisms for this kind of sharing in Ruby. The first, ​ class-level inheritance​ , is common in object-oriented languages. We’ll then look at ​ mixins​ , a technique that is often preferable to inheritance. We’ll wind up with a discussion of when to use each.

好的设计中一个公认的原则是消除不需要的副本。我们努力保证我们应用程序代码中的每一部分内容都只声明了一次。

我们早已看到了类的好处，那就是类的实例都能自动访问类中所有的方法。但这里，我们想处理更多普通的共享类型。假设，我们正在应对一个货运管理应用程序。多数的货运类型都可行，但是所有的形式都共享一些基础的功能(如重量计算等)。我们不想把实现这个功能的代码都复制一份，放到运输类型的实现里面。或者是，我们想要更加通用的功能，能把代码插入的不同的类中。例如，在线商店的功能是计算手推车的营业税，订单的营业税，报价的营业税(sales tax for carts, orders, quotes)等等。重申一下，我们不想在每个地方都复制一遍计算营业税的代码。

在这章中，我们将会讲解Ruby中两种不同的机制实现共享功能。第一种是，继承——在面向对象中很普遍。然后会讲解mixin, 它是优于继承的一种方式。我们最终会讨论何时使用哪一种。
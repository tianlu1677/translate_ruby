第五章 5
========

共享功能: 继承、模块和 Mixin(Sharing Functionality: Inheritance, Modules, and Mixins)
----------------------------

One of the accepted principles of good design is the elimination of unnecessary duplication. We work hard to make sure that each concept in our application is expressed just once in our code.[32]
We’ve already seen how classes help. All the methods in a class are automatically accessible to instances of that class. But there are other, more general types of sharing that we want to do. Maybe we’re dealing with an application that ships goods. Many forms of shipping are available, but all forms share some basic functionality (weight calculation, perhaps). We don’t want to duplicate the code that implements this functionality across the implementation of each shipping type. Or maybe we have a more generic capability that we want to inject into a number of different classes. For example, an online store may need the ability to calculate sales tax for carts, orders, quotes, and so on. Again, we don’t want to duplicate the sales tax code in each of these places.
In this chapter, we’ll look at two different (but related) mechanisms for this kind of sharing in Ruby. The first,  class-level inheritance , is common in object-oriented languages. We’ll then look at  mixins , a technique that is often preferable to inheritance. We’ll wind up with a discussion of when to use each.

公认的好设计原则之一是消除不必要的重复。我们尽量确保应用中每个概念在代码中只声明一次。

我们已看到了类的好处，那就是类的实例都能自动访问类中所有的方法。但还有一些其他的，更多的普通共享类型我们想要处理。假设，我们正在处理一个货运管理应用程序。多数的货运类型都可行，它们都共享一些基础的功能(如重量计算等)。我们不想通过复制代码实现所有运输类型来实现这个功能。更甚至是，我们想把一个更加通用的功能放入到不同的类中。例如，在线商店或许会有的功能是计算手推车的营业税、订单的营业税、报价的营业税等等的需求。重申一下，我们不想在每个地方都复制一遍计算营业税的代码。

在本章中，我们将会探索 Ruby 中对于这种共享类型的两种不同（但有一定联系）机制。第一种是，类级别的继承——在面向对象语言中很普遍。然后会谈一谈 Mixin, 它是与继承相比一种更可取方式。最终，我们会通过讨论揭晓什么时候使用哪一种。


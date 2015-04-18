Chapter 5
====
Sharing Functionality: Inheritance, Modules, and Mixins
====
One of the accepted principles of good design is the elimination of unnecessary duplication. We work hard to make sure that each concept in our application is expressed just once in our code.[32]

We’ve already seen how classes help. All the methods in a class are automatically accessible to instances of that class. But there are other, more general types of sharing that we want to do. Maybe we’re dealing with an application that ships goods. Many forms of shipping are available, but all forms share some basic functionality (weight calculation, perhaps). We don’t want to duplicate the code that implements this functionality across the implementation of each shipping type. Or maybe we have a more generic capability that we want to inject into a number of different classes. For example, an online store may need the ability to calculate sales tax for carts, orders, quotes, and so on. Again, we don’t want to duplicate the sales tax code in each of these places.

In this chapter, we’ll look at two different (but related) mechanisms for this kind of sharing in Ruby. The first, ​ class-level inheritance​ , is common in object-oriented languages. We’ll then look at ​ mixins​ , a technique that is often preferable to inheritance. We’ll wind up with a discussion of when to use each.
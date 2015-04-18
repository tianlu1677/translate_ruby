Chapter 3
====
类、对象和变量(Classes, Objects, and Variables)

From the examples we’ve shown so far, you may be wondering about our earlier assertion that Ruby is an object-oriented language. Well, this chapter is where we justify that claim. We’re going to be looking at how you create classes and objects in Ruby and at some of the ways that Ruby is more powerful than most object-oriented languages.

As we saw, everything we manipulate in Ruby is an object. And every object in Ruby was generated either directly or indirectly from a class. In this chapter, we’ll look in more depth at creating and manipulating those classes.

Let’s give ourselves a simple problem to solve. Let’s say that we’re running a secondhand bookstore. Every week, we do stock control. A gang of clerks uses portable bar-code scanners to record every book on our shelves. Each scanner generates a simple comma-separated value (CSV) file containing one row for each book scanned. The row contains (among other things) the book’s ISBN and price. An extract from one of these files 

从我们之前展示的例子，你可能会怀疑我们之前的论断——Ruby是一门面向对象的语言。那好，这章就是为了证明这个论断。我们将会看到如何在Ruby中创建类和对象，并且在Ruby中相对其他面向对象的语言更强大的部分。

正如我们所说的，在Ruby中我们所操作的都是对象。在Ruby中，每个对象直接或间接的都是隶属于一个类。在本章中，我们会更深入了解创建和操作类。

让我们从解决一个简单问题开始。假设，我们经营一家二手书店，每周我们都会做库存管理。管理员们使用便携式条码扫描仪来记录我们的书架上的每一本书。每个扫描仪对扫描的每本书生成一行内容的文件(CSV)，一行之间的信息用逗号分开。一行包括一本书的ISBN(图书编号)和price(价格)。下面的内容就是从这些文件中抽出的一部分：

```ruby
tut_classes/stock_stats/data.csv
​ 	
"Date","ISBN","Price"​ 	
"2013-04-12","978-1-9343561-0-4",39.45​ 	
"2013-04-13","978-1-9343561-6-6",45.67​ 	
"2013-04-14","978-1-9343560-7-4",36.95
```

我们的任务是处理这些CSV文件，然后计算出每种书有多少本和进货单上书的总价。
不管我们什么时候开始设计面向对象的系统，好的开始时确定出我们要处理的事物。通常，每类事物在最终的程序中都用类来表示，具体的事物转成成类的实例变量。

很明显，我们需要用什么来代表通过扫描仪扫描的数据。每一个实例将会代表特定的一行数据，所有这些对象的集合来代表我们所有获取的数据。

让我们把类称为`BookInStock`.(记住，类名以大写字母开头，方法名通常以小写字母开头)。

```ruby
​class​ BookInStock
​ 	
​end​
```
As we saw in the previous chapter, we can create new instances of this class using ​new​ :
正如我们前一章，我们用`new`来创建一个类`BookInStock`的新实例。
```ruby
a_book = BookInStock.new​ 	
another_book = BookInStock.new
```
After this code runs, we’d have two distinct objects, both of class ​BookInStock​. But, besides that they have different identities, these two objects are otherwise the same—there’s nothing to distinguish one from the other. And, what’s worse, these objects actually don’t hold any of the information we need them to hold.

The best way to fix this is to provide the objects with an ​initialize​ method. This lets us set the state of each object as it is constructed. We store this state in ​ instance variables​ inside the object. (Remember instance variables? They’re the ones that start with an @ sign.) Because each object in Ruby has its own distinct set of instance variables, each object can have its own unique state.

So, here’s our updated class definition:

运行代码后，我们有两个不同的对象，都属于类`BookInStock`。两个对象除了有不同的身份(identites),其他都相同。而且，更糟糕的是，这两个对象没有保存任何我们想要他们保存的信息。

改正这个问题的最好方法是为对象提供初始化(initialize)方法。这样就能在对象创建的时候，为每个类设置状态了。我们在把状态存储在对象内部的实例变量里面。(还记得实例变量吗？他们是以`@`开头的。)因为在Ruby中，每个对象都有它自己的一组实例变量，并能有属于他自己的不同状态。

所以，下面是更新的类的定义:
```ruby
​class​ BookInStock​ 	
  ​def​ initialize(isbn, price)​ 	
    @isbn  = isbn​ 	
    @price = Float(price)​ 	
  ​end​​ 	
​end​
```
​initialize​ is a special method in Ruby programs. When you call ​BookInStock.new​ to create a new object, Ruby allocates some memory to hold an uninitialized object and then calls that object’s ​initialize​ method, passing in any parameters that were passed to ​new​ . This gives you a chance to write code that sets up your object’s state.

For class ​BookInStock​, the ​initialize​ method takes two parameters. These parameters act just like local variables within the method, so they follow the local variable naming convention of starting with a lowercase letter. But, as local variables, they would just evaporate once the ​initialize​ method returns, so we need to transfer them into instance variables. This is very common behavior in an ​initialize​ method—the intent is to have our object set up and usable by the time ​initialize​ returns.

This method also illustrates something that often trips up newcomers to Ruby. Notice how we say ​@isbn = isbn​. It’s easy to imagine that the two variables here, ​@isbn​ and ​isbn​, are somehow related—it looks like they have the same name. But they don’t. The former is an instance variable, and the “at” sign is actually part of its name.

Finally, this code illustrates a simple piece of validation. The ​Float​ method takes its argument and converts it to a floating-point number,[19] terminating the program with an error if that conversion fails. (Later in the book we’ll see how to handle these exceptional situations.) What we’re doing here is saying that we want to accept any object for the ​price​ parameter as long as that parameter can be converted to a float. We can pass in a float, an integer, and even a string containing the representation of a float, and it will work. Let’s try this now. We’ll create three objects, each with different initial state. The ​p​ method prints out an internal representation of an object. Using it, we can see that in each case our parameters got transferred into the object’s state, ending up as instance variables:

在Ruby中，`initialize`是特殊的方法。当你调用`BookInStock.new​`来创建新的对象时，Ruby给未被初始化的对象分配一些内存，然后调用initialize方法，把传递给new的所有参数传递给initialize方法。这样就能让你通过代码来设置对象的状态。

类`BookInStock`的initialize方法有两个参数。这两个参数就像方法中的局部变量，遵循的局部变量命名约定以小写字母开头。一旦initialize方法执行完，他们就像局部变量一样马上消失。因此，我们必须把他们传递给实例变量。这在初始化方法里面是很常见的用法，目的是为了设置对象和等初始化后变量可用。

这个方法也用来举例说明Ruby新手所犯的错误。注意，我们说的 `@isbn = isbn​`。变量 ​`@isbn`​和`isbn`容易被想象有某种联系，因为他们看起来有相同的名字。其实他们是不一样的，`@isbn`是实例变量，`@`符号是它名字的一部分。

最后，这段代码演示了一个简单的验证。`Float`方法获取参数并转成一个浮点数，如果转换失败的话，程序会提示错误并且终止。（在本书的后面，我们会讲如何处理这些异常情况。）这里我们所做的是，只要参数`price`能转化成浮点数，任何对象都会接收`price`参数。它可以是一个浮点，一个整数，甚至是一个包含浮点数的字符串。那我们现在来试试。我们会创建三个拥有不同状态的对象。方法`p`会输出对象的内部描述。用`p`方法，我们可以看到在不同的参数转化成对象的状态，最后变成实例变量的:

这个方法
```ruby
​class​ BookInStock​ 	
  ​def​ initialize(isbn, price)​ 	
    @isbn  = isbn​ 	
    @price = Float(price)​ 	
  ​end​​ 	
​end​​ 	
​ 	
b1 = BookInStock.new(​"isbn1"​, 3)​ 	
p b1​ 	
​ 	
b2 = BookInStock.new(​"isbn2"​, 3.14)​ 	
p b2​ 	
​ 	
b3 = BookInStock.new(​"isbn3"​, ​"5.67"​)​ 	
p b3
```
Produces:
```ruby
#<BookInStock:0x007fac4910f3e0 @isbn="isbn1", @price=3.0>​ 	
#<BookInStock:0x007fac4910f0c0 @isbn="isbn2", @price=3.14>​ 	
#<BookInStock:0x007fac4910eda0 @isbn="isbn3", @price=5.67>
```
Why did we use the ​p​ method to write out our objects, rather than ​puts​ ? Well, let’s repeat the code using ​puts​ :
我们为什么用`p`方法输出我们的对象，而是`puts`方法?让我们用`puts`方法重写一遍:
```ruby
​class​ BookInStock​ 	
  ​def​ initialize(isbn, price)​ 	
    @isbn  = isbn​ 	
    @price = Float(price)​ 	
  ​end​​ 	
​end​
b1 = BookInStock.new(​"isbn1"​, 3)
puts b1

b2 = BookInStock.new(​"isbn2"​, 3.14)​ 	
puts b2​ 	
​ 	
b3 = BookInStock.new(​"isbn3"​, ​"5.67"​)​ 	
puts b3
```
Produces:
```ruby	
#<BookInStock:0x007fb424847468>​ 	
#<BookInStock:0x007fb424847238>​ 	
#<BookInStock:0x007fb424847058>
```
Remember, ​puts​ simply writes strings to your program’s standard output. When you pass it an object based on a class you wrote, it doesn’t really know what to do with it, so it uses a very simple expedient: it writes the name of the object’s class, followed by a colon and the object’s unique identifier (a hexadecimal number). It puts the whole lot inside ​`#<...>`​.

Our experience tells us that during development we’ll be printing out the contents of a ​BookInStock​ object many times, and the default formatting leaves something to be desired. Fortunately, Ruby has a standard message, ​to_s​ , that it sends to any object it wants to render as a string. So, when we pass one of our ​BookInStock​ objects to ​puts​ , the ​puts​ method calls ​to_s​ in that object to get its string representation. So, let’s override the default implementation of ​to_s​ to give us a better rendering of our objects:

牢记，`puts`仅仅输出字符串到你的程序标准输出中。当你向它传递由类生成的对象时候，它不知道如何处理，所以它权宜之计就是输出对象所属类的名称，紧跟着是一个冒号和对象的唯一标识符(十六进制数)。然后把所有这些方法放在`#<...>`里面输出。

在开发中，根据经验，我们需要多次输出对象里的内容(a ​BookInStock​ object)，并且默认格式化我们想要的数据。幸运的是，Ruby中有`to_s`方法，它可以把任何想要输出的对象转化成字符串输出。所以，我们给`puts`方法传递对象时，`puts`方法会调用`to_s`来把对象内容当字符串输出。(So, when we pass one of our ​BookInStock​ objects to ​puts​ , the ​puts​ method calls ​to_s​ in that object to get its string representation)因此，我们覆盖实现默认的to_s方法，而让其更好的显示我们的对象:

```ruby
​class​ BookInStock​ 	
  ​def​ initialize(isbn, price) 	
    @isbn  = isbn​ 	
    @price = Float(price)​ 	
  ​end​
​ 	
  ​def​ to_s​ 	
    ​"ISBN: ​#{@isbn}​, price: ​#{@price}​"​​ 	
  ​end​​ 	
​end​
​ 	
b1 = BookInStock.new(​"isbn1"​, 3)​ 	
puts b1
​ 	
b2 = BookInStock.new(​"isbn2"​, 3.14)​ 	
puts b2
​ 	
b3 = BookInStock.new(​"isbn3"​, ​"5.67"​)​ 	
puts b3
```
Produces:
```ruby	
ISBN: isbn1, price: 3.0​ 	
ISBN: isbn2, price: 3.14​ 	
ISBN: isbn3, price: 5.67
```
There’s something going on here that’s both trivial and profound. See how the values we set into the instance variables ​@isbn​ and ​@price​ in the ​initialize​ method are subsequently available in the ​to_s​ method? That shows how instance variables work—they’re stored with each object and available to all the instance methods of those objects.
这里发生的事情即微不足道却又意义重大。我们是如何在初始化方法中设置实例变量`@isbn`和`@price`的值，让其在to_s方法中可用的？在展示了实例变量是如何起作用的，他们存储在每个对象中并且对这些对象中的实例方法都是可用的。

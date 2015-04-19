第三章
===========

类、对象和变量(Classes, Objects, and Variables)
--------------------------------------------


从之前展示的例子，可能会怀疑我们之前的论断 —— Ruby 是一门面向对象的语言。那么本章就是为了证明这个。接下来展示在 Ruby 中创建类和对象，以及比其他面向对象语言更强大的部分。

在 Ruby 中我们所操作的都是对象。每个对象直接或间接都属于一个类。在本章中，将会更深入了解创建类和操作类。

从解决一个简单问题开始。假设，我们经营一家二手书店，每周我们都会做库存管理。管理员们使用便携式条码扫描仪来记录我们的书架上的每一本书。每个扫描仪对扫描的每本书生成一行内容的文件(CSV)，一行之间的信息用逗号分开。一行包括一本书的 ISBN (图书编号)和 price (价格)。下面的内容就是从这些文件中抽出的一部分：

```Ruby
# tut_classes/stock_stats/data.csv
​
"Date","ISBN","Price"​
"2013-04-12","978-1-9343561-0-4",39.45​
"2013-04-13","978-1-9343561-6-6",45.67​
"2013-04-14","978-1-9343560-7-4",36.95
```

我们的任务是处理这些CSV文件，然后计算出每种书有多少本和进货单上书的总价。
不管什么时候设计面向对象系统，确定出我们要处理的事物是好的开始。通常，每类事物在最终的程序中都用类来表示，具体的事物转成成类的实例。

很明显，通过扫描仪扫入的数据需要用类来表示。每个对象将会代表特定的一行数据，所有这些对象的集合来代表我们所有获取的数据。

这个类称为`BookInStock`。(记住，类名以大写字母开头，方法名通常以小写字母开头)。

```ruby
​class​ BookInStock

​end​
```


As we saw in the previous chapter, we can create new instances of this class using ​new​ :
正如前一章一样，用`new`来创建一个类`BookInStock`的新对象。

```ruby
a_book = BookInStock.new​
another_book = BookInStock.new
```

代码运行后，会两个不同的对象，都属于类`BookInStock`。两个对象除了有不同的身份(identites)外，其他都相同。而且，更糟糕的是，这两个对象没有保存任何我们想要他们保存的信息。

改正这个问题的最好方法是为对象提供初始化(`initialize`)方法。这样就能在对象创建的时候，为每个类设置状态了。我们在把状态存储在对象内部的实例变量里面。(还记得实例变量吗？他们是以 `@` 开头。) 因为在Ruby中，每个对象都有它自己的一组实例变量，并有属于他自己的不同状态。

所以，下面是重新定义的类:

```ruby
​class​ BookInStock​
  ​def​ initialize(isbn, price)​
    @isbn  = isbn​
    @price = Float(price)​
  ​end​​
​end​
```

在 Ruby 中，`initialize` 是特殊的方法。当你调用 `BookInStock.new​` 来创建新的对象时，Ruby 分配一些内存来保存未初始化的对象，然后调用`initialize`方法，把传递给方法`new`的所有参数传递给 `initialize` 方法。这样就可以通过代码来设置对象的状态。

类 `BookInStock` 的 `initialize` 方法有两个参数。这两个参数就像方法中的局部变量，遵循局部变量以小写字母开头命名的约定。一旦 `initialize` 方法执行完，参数就像局部变量一样马上消失。因此，必须把参数传递给实例变量。这在初始化方法里面是很常见的用法，目的是为了设置对象和等初始化之后变量可用。

这个方法也用来举例说明 Ruby 新手所犯的错误。注意，我们说的 `@isbn = isbn​`。变量 ​`@isbn`​和`isbn`容易被想象有某种联系，因为他们看起来有相同的名字。其实他们是不一样的，`@isbn`是实例变量，`@`符号是它名字的一部分。

最后，这段代码演示了一个简单的验证。`Float` 方法获取参数并转成一个浮点数，如果转换失败的话，程序会提示错误并且终止。（在本书的后面，我们会讲如何处理这些异常情况。）这里我们所做的是，接受参数 `price`  能转化成浮点数的任何对象。对象可以是一个浮点，一个整数，甚至是一个包含浮点数的字符串。现在，创建了三个初始化不同状态的对象。方法 `p` 会输出对象内部的表现。用`p`方法，我们可以看到在不同的参数转化成对象的状态，最后变成实例变量的:

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

结果是：

```ruby
#<BookInStock:0x007fac4910f3e0 @isbn="isbn1", @price=3.0>​
#<BookInStock:0x007fac4910f0c0 @isbn="isbn2", @price=3.14>​
#<BookInStock:0x007fac4910eda0 @isbn="isbn3", @price=5.67>
```


我们为什么用 `p` 方法输出我们的对象，而是 `puts` 方法？让我们用 `puts` 方法重写一遍:

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

结果是：

```ruby
#<BookInStock:0x007fb424847468>​
#<BookInStock:0x007fb424847238>​
#<BookInStock:0x007fb424847058>
```

Remember, ​puts​ simply writes strings to your program’s standard output. When you pass it an object based on a class you wrote, it doesn’t really know what to do with it, so it uses a very simple expedient: it writes the name of the object’s class, followed by a colon and the object’s unique identifier (a hexadecimal number). It puts the whole lot inside ​`#<...>`​.

Our experience tells us that during development we’ll be printing out the contents of a ​BookInStock​ object many times, and the default formatting leaves something to be desired. Fortunately, Ruby has a standard message, ​to_s​ , that it sends to any object it wants to render as a string. So, when we pass one of our ​BookInStock​ objects to ​puts​ , the ​puts​ method calls ​to_s​ in that object to get its string representation. So, let’s override the default implementation of ​to_s​ to give us a better rendering of our objects:

牢记，`puts` 仅仅输出字符串到你的程序标准输出中。当你向它传递由类生成的对象时候，它不知道如何处理，所以它权宜之计就是输出对象所属类的名称，紧跟着是一个冒号和对象的唯一标识符(十六进制数)。然后把所有内容放在`#<...>`里面输出。

根据经验，在开发中需要多次输出 ` ​BookInStock` 对象里面的内容，并且默认转化我们想要的格式。幸运的是，Ruby 中有 标准的信息转化方法 `to_s` ，它可以把任何想要输出的对象转化成字符串输出。所以，给`puts`方法传递对象时，`puts` 方法会调用 `to_s` 来把对象内容当字符串输出。因此，我们重写默认的 `to_s` 方法，让其更好的输入对象:

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

结果是：

```ruby
ISBN: isbn1, price: 3.0​
ISBN: isbn2, price: 3.14​
ISBN: isbn3, price: 5.67
```

这里发生的事情即微不足道却又意义重大。我们是如何在初始化方法中设置实例变量`@isbn`和`@price`的值，让其在`to_s`方法中可用的?在展示了实例变量是如何起作用的，他们存储在每个对象中并且对这些对象中的实例方法都是可用的。

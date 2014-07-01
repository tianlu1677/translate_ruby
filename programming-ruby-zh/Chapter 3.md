Chapter 3
====
Classes, Objects, and Variables
====

From the examples we’ve shown so far, you may be wondering about our earlier assertion that Ruby is an object-oriented language. Well, this chapter is where we justify that claim. We’re going to be looking at how you create classes and objects in Ruby and at some of the ways that Ruby is more powerful than most object-oriented languages.

As we saw, everything we manipulate in Ruby is an object. And every object in Ruby was generated either directly or indirectly from a class. In this chapter, we’ll look in more depth at creating and manipulating those classes.

Let’s give ourselves a simple problem to solve. Let’s say that we’re running a secondhand bookstore. Every week, we do stock control. A gang of clerks uses portable bar-code scanners to record every book on our shelves. Each scanner generates a simple comma-separated value (CSV) file containing one row for each book scanned. The row contains (among other things) the book’s ISBN and price. An extract from one of these files 
```ruby
tut_classes/stock_stats/data.csv
​ 	
"Date","ISBN","Price"​ 	
"2013-04-12","978-1-9343561-0-4",39.45​ 	
"2013-04-13","978-1-9343561-6-6",45.67​ 	
"2013-04-14","978-1-9343560-7-4",36.95
```
Our job is to take all the CSV files and work out how many of each title we have, as well as the total list price of the books in stock.

Whenever you’re designing OO systems, a good first step is to identify the ​things​ you’re dealing with. Typically each type of thing becomes a class in your final program, and the things themselves are instances of these classes.

It seems pretty clear that we’ll need something to represent each data reading captured by the scanners. Each instance of this will represent a particular row of data, and the collection of all of these objects will represent all the data we’ve captured.

Let’s call this class ​BookInStock​. (Remember, class names start with an uppercase letter, and method names normally start with a lowercase letter.)
```ruby
​class​ BookInStock
​ 	
​end​
```
As we saw in the previous chapter, we can create new instances of this class using ​new​ :
```ruby
a_book = BookInStock.new​ 	
another_book = BookInStock.new
```
After this code runs, we’d have two distinct objects, both of class ​BookInStock​. But, besides that they have different identities, these two objects are otherwise the same—there’s nothing to distinguish one from the other. And, what’s worse, these objects actually don’t hold any of the information we need them to hold.

The best way to fix this is to provide the objects with an ​initialize​ method. This lets us set the state of each object as it is constructed. We store this state in ​ instance variables​ inside the object. (Remember instance variables? They’re the ones that start with an @ sign.) Because each object in Ruby has its own distinct set of instance variables, each object can have its own unique state.

So, here’s our updated class definition:
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
---
layout: post
title: "Super is Super Duper"
date: 2015-10-19 22:03:52 -0400
comments: true
categories: super, module, object orientation, class, parent class, inheritance
---

As we build programs, we'll often find ourselves revising the blocks and compoments within our method bodies so we can improve their functionality, abstract them away, or bolster them for upscaling. By the same token, we'll break out functionality into multiple methods within a class, or even into new classes and modules to make the original methods more widely available to other objects in our program.

Often, several classes or objects in a program will share method names (the initialize method in classes, as an obvious example), but by calling a method on a certain object we give Ruby the necessary lookup directions to access the right code. Knowing how method lookup works can be quite helpful, even if only so that you're aware of what you're calling when and where you call it. It's pretty straightforward stuff, but as a recap:

When an object receives a message, it first looks within: 

  * Its own class to see if the method is contained there; 
  * If not, it moves on to modules mixed into its class (in reverse order of their inclusion);
  * Next, its superclass;
  * Then, modules mixed into the superclass (again in reverse order of their inclusion);
  * and then all the way up to Object and BasicObject.

A Ruby function called "super" makes method lookup even more interesting. Super can be cleverly employed through modules or class inheritance to yield some potentially useful results. When you call it within a method, Ruby will work its way up the method lookup chain to find another method with the same name, and will run the code contained there.

Here's a quick basic example of an instance where a class and a module share method names, *receive_treat*, enabling both methods to be mixed together when super is called: 

``` ruby USING RUBY'S SUPER KEYWORD
module GiveTreat
  def receive_treat
    puts "One treat for you!"
  end
end

class Dog
  include GiveTreat
  def receive_treat
    puts "Give me a treat!"
    puts "Now, dammit!"
    super
    puts "I'm one happy pup!"
  end
end

happy_pup = Dog.new
happy_pup.receive_treat

```

Luckily for this pup, the output would be: 

*Give me a treat!* / *Now, dammit!* / *One treat for you!* / *I'm one happy pup!*


Another quick one, this time with class inheritance instead of a module:

``` ruby USING RUBY'S SUPER KEYWORD
class Animal
  def eat
    "I eat"
  end
end

class Rat < Animal
  def eat
    super + " pizza"
  end
end

class Bird < Animal
  def eat
    super + " worms"
  end
end

class Dog < Animal
  def eat
    super + " puppy chow"
  end
end

puts Rat.new.eat
puts Bird.new.eat
puts Dog.new.eat

```

These return: 

*I eat pizza* / *I eat worms* / *I eat puppy chow* 

So, these are pretty silly, for sure, and it begs the question: when does super actually get used? Even more puzzling to me, *why would I **ever** use this*?

Further reading demonstrated that super can be somewhat more useful (as most things are in coding), if used like this, perhaps:

When a class object is inherited from a parent class, super can be used to instantiate the new class object with  additional or modified instance variables. Let's take, for example, a parent cafeteria object in a school cafeteria app that other cafeteria objects might inherit from:

``` ruby CAFETERIA PARENT OBJECT
class Cafeteria
  def initialize
    @cooks = 10
    @stoves = 5
    @pots = 10
    @pans = 10
  end
    
  def make_food
    ...    
  end

  def clean_dishes
    ...
  end
end

class FlatironCafeteria < Cafeteria
  def initialize
    super
    @stoves = 1
    @microwave = 1
    @coffee_maker_that_sort_of_works = 1
  end
end

```

Yielding:

```ruby CAFETERIA OBJECTS
  Cafeteria.new:
  <Cafeteria:0x007fb67c86e360 @cooks=10, @stoves=5, @pots=10, @pans=10> 

  FlatironCafeteria.new:
  <FlatironCafeteria:0x007fb5cc3bfb58 @cooks=10, @stoves=1, @pots=10, @pans=10, @microwave=1, @coffee_maker_that_sort_of_works=1> 
```

In this case, when FlatironCafeteria is initialized using super (so Ruby knows to check the intialize method within FlatironCafeteria *and* Cafeteria), FlaitronCafeteria is initalized with all of Cafeteria's objects and a few newer instance variables of its own -- mainly that coffee maker.

If we didn't pass super in the FlatironCafeteria initialize method, though, the result would have been:

```ruby CAFETERIA OBJECTS
Cafeteria.new
<Cafeteria:0x007fc954866e40 @cooks=10, @stoves=5, @pots=10, @pans=10> 
FlatironCafeteria.new
<FlatironCafeteria:0x007fc95486fec8 @microwave=1, @coffee_maker_that_sort_of_works=1> 
```

As you can see, FlatironCafeteria received none of Cafeteria's instance variables. Depending on our program, we may want new class objects to be initialized with their parent class's instance variables -- super makes that happen.

These are very basic portrayals of super usage, but this not-so-little tool can certainly come in handy when building additional functionality into our classes, modules, and programs. 

To conclude:

It's a bird! It's a plane! It's... **super** *!*

{% img center http://sensacionalista.uol.com.br/wp-content/uploads/2013/04/superman-cat-1.jpeg  400 'SuperCat' 'An image of a cat that can save the day' %}




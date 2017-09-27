---
title: python3 learning 12
date: 2017-09-25 18:33:39
tags: python3
---
## Objects
In the last few chapters, we’ve been looking at different ways of organizing data and programs and collecting things together. We have seen that lists are a way to collect variables (data) together, and functions are a way to collect some code together into a unit that you can use over and over again. 

Objects take the idea of collecting things together one step further. Objects are a way to collect functions and data together. This is a very useful idea in programming, and it’s used in many, many programs. In fact, if you look under the hood in Python, almost everything is an object. In programming terms, we say Python is object oriented. That means that it’s possible (in fact, quite easy) to use objects in Python. It isn’t necessary to create your own objects, but it makes many things easier. 

In this chapter, we’ll learn what objects are and how to create and use them. In later chapters, when we start doing graphics, we’ll be using objects a lot.

### Objects in the real world
What’s an object? If we were not talking about programming, and I asked you that question, we might have a conversation like this:  
![](https://github.com/changemyheart/Pictures/blob/master/what's%20object.png?raw=true)
That’s a good start at defining what an object is in Python, too. Take a ball, for example. You can do things to a ball, like pick it up, throw it, kick it, or inflate it (for some balls). We call these actions. You can also describe a ball by telling me its color, size, and weight. These are attributes of a ball. 

>You can describe an object by describing its characteristics or attributes. One of the attributes of a ball is its shape. Most balls have a round shape. Other examples of attributes are color, size, weight, and cost. Another word for attributes is properties.

Real objects in the real world have  
&emsp;&emsp;■ things that you can do to them (actions).  
&emsp;&emsp;■ things that describe them (attributes or properties).

In programming, we have the same kind of thing. 

### Objects in Python
In Python, the characteristics, or “things you know” about an object, are also called attributes, so that should be easy to remember. In Python, the actions, or “things you can do” to an object, are called methods. 

If you were to make a Python version or model of a ball, the ball would be an object and it would have attributes and methods. 

The ball’s attributes would look like this:
```python
ball.color
ball.size
ball.weight
```
Those are all things you can describe about the ball.

The ball’s methods would look like this:
```python
ball.kick()
ball.throw()
ball.inflate()
```
Those are all things you can do to the ball.

#### What are attributes?
Attributes are all things you know (or can find out) about the ball. The ball’s attributes are chunks of information—numbers, strings, and so on. Sound familiar? Yes, they’re variables. They’re just variables that are included inside the object.
You can display them:
```python
print(ball.size)
```
You can assign values to them:
```python
ball.color = 'green'
```
You can assign them to regular, non-object variables:
```python
myColor = ball.color
```
You can also assign them to attributes in other objects: 
```python
myBall.color = yourBall.color
```

#### What are methods?
Methods are things you can do with an object. They’re chunks of code that you can call to do something. Sound familiar? Yes, methods are just functions that are included inside the object. 

You can do all the things with methods that you can do with any other function, including passing arguments and returning values. 

### Object = attributes + methods
So objects are a way of collecting together attributes and methods (things you know, and things you can do) for a thing. Attributes are information, and methods are actions.

### What’s the dot?
In our previous ball examples, you probably noticed the dot between the name of the object and the name of the attribute or method. That’s just the Python notation for using the attributes and methods of an object: `object.attribute` or `object.method()`. Simple as that. It’s called dot notation, and it’s used in many programming languages.

Now we have the big picture about objects. Let’s start making some!

### Creating objects
There are two steps to creating an object in Python. 

The first step is to define what the object will look like and act like—its attributes and methods. But creating this description doesn’t actually create an object. It’s kind of like the blueprints for a house. The blueprints tell you exactly what the house will look like, but a blueprint isn’t a house. You can’t live in a blueprint. You can just use it to build an actual house. In fact, you can use the blueprint to make many houses. 

In Python the description or blueprint of an object is called a class.

The second step is to use the class to make an actual object. The object is called an instance of that class. 

Let’s look at an example of making a class and an instance.
```python
class Ball:    # This tells Python we’re making a class
    
    def bounce(self):
        if self.direction == "down":
            self.direction = "up"
    # This is a method
```
In above, we have a class definition for a ball with one method: `bounce()`. But what about attributes? Well, attributes don’t really belong to the class, they belong to each instance. That’s because each instance can have different attributes. 

There are a couple of ways we can set the instance attributes. We’ll see both ways in the following sections.

#### Creating an instance of an object
As we mentioned before, a class definition isn’t an object. It’s just the blueprints. Now let’s build a house. 

If we want to create an instance of a Ball, we do it like this:
```python
>>> myBall = Ball()
```
Our ball does not have any attributes yet, so let’s give it some:
```python
>>> myBall.direction = "down"
>>> myBall.color = "green"
>>> myBall.size = "small"
```
This is one of the ways to define attributes for the object. We’ll see the other way in the next section.

Now, let’s try out one of the methods. Here’s how we’d use the `bounce()` method:
```python
>>> myBall.bounce()
```
Let’s put this all together into a program, with some print statements to see what’s going on.
```python
class Ball:

    def bounce(self):
        if self.direction == "down":
            self.direction = "up"
# Here’s our class, same as before

myBall = Ball() # Makes an instance of our class

myBall.direction = "down"
myBall.color = "red"
myBall.size = "small"
# Sets some attributes
           
print("I just created a ball.") 
print("My ball is", myBall.size)
print("My ball is", myBall.color)
print("My ball's direction is", myBall.direction)
print("Now I'm going to bounce the ball")
# Prints the object’s attributes
print()

myBall.bounce() # Uses a method
print("Now the ball's direction is", myBall.direction)
```
If we run the program above, we should see this:
```
>>> ========================== RESTART ==========================
>>> 
I just created a ball. 
My ball is small
My ball is red
My ball's direction is down
Now I'm going to bounce the ball # Now we bounce() the ball
Now the ball's direction is up   # It changed direction, from down to up
>>> 
```
Notice that after we called the `bounce()` method, the ball’s `direction` changed from `down` to `up`, which is exactly what the code in the `bounce()` method is supposed to do.

#### Initializing an object
When we created our ball object, it didn’t have anything filled in for the size, color, or direction. We had to fill those in after we created the object. But there’s a way to set the properties of an object when it’s being created. This is called initializing the object. 

>Initializing means “getting something ready at the start.” When we initialize something in software, we make it ready to use by getting it into the state or condition that we want.

When you create the class definition, you can define a special method called `__init__()` that will run whenever a new instance of the class is created. You can pass arguments to the `__init__()` method to create the instance with its properties set however you want.
```python
class Ball:
    def __init__(self, color, size, direction):
        self.color = color
        self.size = size
        self.direction = direction
    # Here’s the __init__() method

    def bounce(self):
        if self.direction == "down":
            self.direction = "up"
myBall = Ball("red", "small", "down") # Attributes are passed in as arguments to __init__()
print("I just created a ball.")
print("My ball is", myBall.size)
print("My ball is", myBall.color)
print("My ball's direction is ", myBall.direction)
print("Now I'm going to bounce the ball")
print()
myBall.bounce()
print("Now the ball's direction is", myBall.direction)
```

If you say `print(myBall)`, you get something weird like this:  
`<__main__.Ball instance at 0x00BB83A0>`

To change that, put in a method called `__str__()`.

Make it return what you want printed. Then, every time you use `print(myBall)`, it’ll say what you want.

It’s one of the“magic” `__xxxx__()` class methods in Python!

#### A “magic” method: `__str__()`
Objects in Python have some “magic” methods. They’re not really magic, of course! They’re just some methods that Python includes automatically when youcreate any class. Python programmers usually call them special methods.

We already saw the `__init__()` method that initializes an object when it’s created. Every object has an `__init__()` method built in. If you don’t put one in your class definition, the built-in one takes over, and all it does is create the object.

Another special method is `__str__()`, which tells Python what to display when you `print` an object. By default, Python tells you  
&emsp;&emsp;■ where the instance is defined (in Carter’s case `__main__`, which is the main part of the program).  
&emsp;&emsp;■ the class name (`Ball`).  
&emsp;&emsp;■ the memory location where the instance is being stored (that’s the `0x00BB83A0` part).

But if you want print to display something different for your object, you can define your own `__str__()`, which will override the built-in one.
```python
class Ball:
    def __init__(self, color, size, direction):    
        self.color = color                         
        self.size = size                           
        self.direction = direction

    def __str__(self):
        msg = "Hi, I'm a " + self.size + " " + self.color + " ball!"  
        return msg
    # Here’s the __str__() method

myBall = Ball("red", "small", "down")              
print(myBall)
```
Now, if we run the program above, here’s what we get:
```
>>> ================= RESTART =================
>>> 
Hi, I'm a small red ball!
>>>
```
That looks a lot more friendly than `<__main__.Ball instance at 0x00BB83A0>`, don’t you think?

#### What’s “self”?
You might have noticed that the term “self” shows up in a few places in the class attributes and method definitions, like this:
```python
def bounce(self):
```
What does `self` mean? Well, remember that we said you could use blueprints to build more than one house? You can also use a class to create more than one instance of an object, like this:
```python
cartersBall = Ball("red", "small", "down") 
warrensBall = Ball("green", "medium", "up")
# Creating two instances of the Ball class
```
When we call a method for one of these instances, like this,
```python
warrensBall.bounce()
```
the method has to know which instance called it. Is it `cartersBall` that needs to bounce, or `warrensBall`? The `self` argument is what tells the method which object called it. It’s called the instance reference.

But wait a minute! When we called the method, there was no argument in the parentheses of `warrensBall.bounce()`, but there’s a `self` argument in the method. Where did the `self` argument come from, if we didn’t pass anything? That’s another little bit of “magic” that Python does with objects. When you call a class method, the information about which instance called—the instance reference—is automatically passed to the method. 

It’s like writing this:
```python
Ball.bounce(warrensBall)
```
In this case, we told the `bounce()` method which ball to bounce. In fact, this code will work too, because that is exactly what Python does behind the scenes when you write `warrensBall.bounce()`.  

>By the way, the name `self` has no special meaning in Python. That’s just 
the name everybody uses for the instance reference. It’s another one of those conventions that make your code easier to read. You could name the instance variable whatever you want, but I strongly suggest you follow the convention and use `self`—it’ll make things much less confusing.

### An example class—HotDog
For this example, we’ll assume that hot dogs always have a bun. (It’s too messy otherwise.) We’ll give our hot dog some attributes and some methods. 

These are the attributes:  
&emsp;&emsp;■ `cooked_level`—A number that lets us know how long the hot dog has been cooked. We’ll use 0–3 for raw, over 3 for medium, over 5 for well-done, and anything over 8 will be charcoal! Our hot dogs will start out raw.  
&emsp;&emsp;■ `cooked_string`—A string describing how well-done the hot dog is.  
&emsp;&emsp;■ `condiments`—A list of what’s on the hot dog, like ketchup, mustard, and so on.

These are the methods:  
&emsp;&emsp;■ `cook()`—Cooks the hot dog for some period of time. This will make the hot dog more well-done.  
&emsp;&emsp;■ `add_condiment()`—Adds condiments to the hot dog.  
&emsp;&emsp;■ `__init__()`—Creates our instance and sets the default properties.  
&emsp;&emsp;■ `__str__()`—Makes the print look nicer.

First, we need to define the class. Let’s start with the `__init__()` method, which will set the default attributes for a hot dog:
```python
class HotDog:
    def __init__(self):
        self.cooked_level = 0
        self.cooked_string = "Raw"
        self.condiments = []
```
We start with a raw hot dog and no condiments.

Now, let’s make a method to cook our hot dog:
```python
  def cook(self, time):
        self.cooked_level = self.cooked_level + time # Increases the cooked level by the amount of time
        if self.cooked_level > 8:
            self.cooked_string = "Charcoal"
        elif self.cooked_level > 5:
            self.cooked_string = "Well-done"
        elif self.cooked_level > 3:
            self.cooked_string = "Medium"
        else:
            self.cooked_string = "Raw"
        # Sets the strings for the different cooked levels
```
Before we go any further, let’s test this part. First, we need to create an instance of a hot dog, and we’ll check the attributes, too.
```python
myDog = HotDog()
print(myDog.cooked_level)
print(myDog.cooked_string)
print(myDog.condiments)
```
Let’s put this together into a program and run it.
```python
class HotDog:
    def __init__(self):
        self.cooked_level = 0
        self.cooked_string = "Raw"
        self.condiments = []
    def cook(self, time):
        self.cooked_level = self.cooked_level + time
        if self.cooked_level > 8:                     
            self.cooked_string = "Charcoal"             
        elif self.cooked_level > 5:                     
            self.cooked_string = "Well-done"            
        elif self.cooked_level > 3:                     
            self.cooked_string = "Medium"               
        else:                                           
            self.cooked_string = "Raw"                  
myDog = HotDog()
print(myDog.cooked_level)
print(myDog.cooked_string)
print(myDog.condiments)
```
>Another convention in Python is that the name of a class always starts with an uppercase (capital) letter. So far we have seen `Ball` and `HotDog`, so we have been following the convention. 

Now, run the code above and see what you get. It should look like this:
```python
>>> 
0   # The cooked_level
Raw # The cooked_string
[]  # The condiments
>>> 
```
We see that the attributes are `cooked_level = 0`, `cooked_string = "Raw"`, and `condiments` is empty.

Now, let’s test the `cook()` method.
```python
print("Now I'm going to cook the hot dog")    
myDog.cook(4) # Cooks the hot dog for 4 minutes
print(myDog.cooked_level)
print(myDog.cooked_string)
# Checks the new cooked attributes
```
Run the program again. Now, the output should look like this:
```python
>>> 
0
Raw
[]
Now I'm going to cook the hot dog
4
Medium
>>> 
```
So our `cook()` method seems to work. The `cooked_level` went from `0` to `4`, and the string updated too (from `Raw` to `Medium`).

Let’s try adding some condiments. We need a new method for that. We could also add our `__str__()` function so it’ll be easier to print the object. Edit the program so it looks like following program.
```python
class HotDog:  
    def __init__(self):
        self.cooked_level = 0
        self.cooked_string = "Raw"
        self.condiments = []
  
    def __str__(self):
        msg = "hot dog"
        if len(self.condiments) > 0: 
            msg = msg + " with "
        for i in self.condiments:
            msg = msg+i+", "
        msg = msg.strip(", ")
        msg = self.cooked_string + " " + msg + "."
        return msg
    # Defines the new __str__() method

    def cook(self, time):
        self.cooked_level=self.cooked_level+time
        if self.cooked_level > 8:
            self.cooked_string = "Charcoal"
        elif self.cooked_level > 5:
            self.cooked_string = "Well-done"
        elif self.cooked_level > 3:
            self.cooked_string = "Medium"
        else:
            self.cooked_string = "Raw"

    def addCondiment(self, condiment): 
        self.condiments.append(condiment)
    # Defines the new add_condiments() method

myDog = HotDog()  # Creates the instance
print(myDog)
print("Cooking hot dog for 4 minutes...")
myDog.cook(4)
print(myDog)
print("Cooking hot dog for 3 more minutes...")
myDog.cook(3)
print(myDog)
print("What happens if I cook it for 10 more minutes?")
myDog.cook(10)
print(myDog)
print("Now, I'm going to add some stuff on my hot dog")
myDog.addCondiment("ketchup")
myDog.addCondiment("mustard")
print(myDog)
# Tests to see if everything is working
```
Run the program and see what you get. It should look like this:
```
>>> ================================ RESTART ================================
>>> 
Raw hot dog.
Cooking hot dog for 4 minutes...
Medium hot dog.
Cooking hot dog for 3 more minutes...
Well-done hot dog.
What happens if I cook it for 10 more minutes?
Charcoal hot dog.
Now, I'm going to add some stuff on my hot dog
Charcoal hot dog with ketchup, mustard.
>>>  
```
The first part of the program creates the class. The second part tests the methods to cook our virtual hot dog and add some condiments. But judging by that last couple of lines, I think we cooked it too much. What a waste of ketchup and mustard!

### Hiding the data
You might have realized that there are two ways we can view or change the data (attributes) inside an object. We can either access them directly, like this:
```python
myDog.cooked_level = 5
```
or we can use a method that modifies the attribute, like this:
```python
myDog.cook(5)
```
If the hot dog started out raw (`cooked_level = 0`), these would both do the same thing. They’d set the `cooked_level` to 5. So why did we bother making a method to do this? Why not just do it directly?

I can think of at least two reasons:  
&emsp;&emsp;■ If we were accessing the attributes directly, then cooking the hot dog would require at least 2 parts: changing the cooked_level and changing the cooked_string. With a method, we just make one method call, and it does everything we need.  
&emsp;&emsp;■ If we were accessing the attributes directly, we could do something like this:  
```python
cooked_level = cooked_level - 2
```
That would make the hot dog less cooked than it was before. But you can’t uncook ahot  dog!  So  that  doesn’t  make  sense.  Using  a  method,  we  can  make  sure  that  the `cooked_level` only increases and never decreases. 

>In programming terms, restricting the access to an object’s data so you can only get it or change it by using methods is called data hiding. Python doesn’t have any way to enforce data hiding, but you can write code that follows this rule if you want to.

So far, we have seen that objects have attributes and methods. We have seen how to create objects and how to initialize them with a special method called `__init__()`. We have also seen another special method called `__str__()` that makes our objects print more nicely. 

### Polymorphism and inheritance
Next, we’re going to look at the two aspects of objects that are probably the most important: polymorphism and inheritance. Those are two big long words, but they make objects very useful. I’ll clearly explain what they mean in the next sections. 

#### Polymorphism—same method, different behavior
Very simply, polymorphism means that you can have two (or more) methods with the same name for different classes. These methods can behave differently, depending on which class they’re applied to. 

For example, let’s say you were making a program to practice geometry, and you needed to calculate the area of different shapes, like triangles and squares. You might create two classes, like this: 
```python
class Triangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height
  
    def getArea(self):
        area = self.width * self.height / 2.0
        return area
class Square:
    def __init__(self, size):
        self.size = size
    def getArea(self):
        area = self.size * self.size 
        return area
```
Both the `Triangle` class and the `Square` class have a method called `getArea()`. So if we had an instance of each class, like this,
```python
>>> myTriangle = Triangle(4, 5)
>>> mySquare = Square(7)
```
then we could calculate the area of either one using `getArea()`:
```python
>>> myTriangle.getArea()
10.0
>>> mySquare.getArea()
49
```
We used the method name `getArea()` for both shapes, but the method did something different for each shape. This is an example of polymorphism.

#### Inheritance—learning from your parents
In the real (nonprogramming) world, people can inherit things from their parents or other relatives. You can inherit traits like red hair, or you can inherit stuff like money or property. 

In object-oriented programming, classes can inherit attributes and methods from other classes. This allows you to have whole “families” of classes that share common attributes and methods. That way, you don’t have to start from scratch every time you want to add a member to the family.
![](https://github.com/changemyheart/Pictures/blob/master/family.png?raw=true)
A class that inherits attributes or methods from another class is called a derived class or subclass. An example will help explain this.

Imagine we’re making a game where the player can pick up various things along the way, like food, money, or clothing. We could make a class called `GameObject`. The `GameObject` class would have attributes like `name` (for example, “coin”, “apple”, or “hat”) and methods like `pickUp()` (which would add the coin to the player’s collection of objects). All game objects would have these common methods and attributes.

Then, we could make a subclass for coins. The `Coin` class would be derived from `GameObject`. It would inherit the attributes and methods of `GameObject`, so the `Coin` class would automatically have a `name` attribute and a `pickUp()` method. The `Coin` class would also need a `value` attribute (how much the coin is worth) and a `spend()` method (so you could use the coin to buy something).

Let’s see what the code might look like for these classes.
```python
class GameObject:
    def __init__(self, name):
        self.name = name
  
    def pickUp(self, player):
        # put code here to add the object
        # to the player's collection
    # Defines GameObject class

class Coin(GameObject): # Coin is a subclass of GameObject
    def __init__(self, value):
        GameObject.__init__(self) # In __init__(), inherit GameObject’s init and add stuff to it
        self.value = value

    def spend(self, buyer, seller):
        # put code here to remove the coin
        # from the buyer's money and
        # add it to the seller's money
    # A new spend() method for the Coin class
```

### Thinking ahead
In the last example, we didn’t put any real code in the methods, just some comments explaining what the methods would do. It’s a way of planning or thinking ahead for what you’ll add later. The actual code would depend on how the game worked. Programmers often do this as a way to organize their thoughts when they’re writing more complex code. The “empty” functions or methods are called code stubs. 

If you tried to run the previous example, you’d get an error, because a function definition can’t be empty. 

The Python `pass` keyword is used as a placeholder when you want to make a code stub. So the code should really look like this:
```python
class Game_object:
    def __init__(self, name):
        self.name = name
    def pickUp(self):
        pass
        # put code here to add the object 
        # to the player's collection
class Coin(Game_object):
    def __init__(self, value):
        Game_object.__init__(self)
        self.value = value
    def spend(self, buyer, seller):
        pass
        # put code here to remove the coin 
        # from the buyer's money and  
        # add it to the seller's money
```
I’m not going to give more detailed examples using objects, polymorphism, and inheritance in this chapter. We’ll see many examples of objects and how they’re used as we go through the rest of this book. You’ll get a much better understanding of how to use objects when we use them in real programs, like games.

---

## What did you learn?
In this chapter, you learned about  
&emsp;&emsp;■ what objects are.  
&emsp;&emsp;■ attributes and methods.  
&emsp;&emsp;■ what a class is.  
&emsp;&emsp;■ creating an instance of a class.  
&emsp;&emsp;■ special methods: `__init__()` and `__str__()`.  
&emsp;&emsp;■ polymorphism.  
&emsp;&emsp;■ inheritance.  
&emsp;&emsp;■ code stubs.

## Test your knowledge
1. What keywords do you use to define a new object type?
2. What are attributes?
3. What are methods?
4. What’s the difference between a class and an instance?
5. What name is usually used for the instance reference in a method?
6. What’s polymorphism?
7. What’s inheritance?

## Try it out
1. Make a class definition for a `BankAccount`. It should have attributes for its name (a string), account number (a string or integer), and balance (a float). It should have methods to display the balance, make deposits, and make withdrawals.
2. Make a class called `InterestAccount` that earns interest. It should be a subclass of `BankAccount` (so it inherits the attributes and methods). It should also have an attribute for interest rate, and a method to add interest. To keep things simple, assume that the `addInterest()` method will be called once each year to calculate the interest and update the balance.
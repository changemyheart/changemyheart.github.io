---
title: python3 learning 13
date: 2017-09-27 19:23:01
tags: python3
---
## Modules
This is the last chapter that talks about ways of collecting things together. We have already learned about lists, functions, and objects. In this chapter, we’ll learn about modules. In the next chapter, we’ll use a module called Pygame to start drawing some graphics.
<!-- more -->

### What’s a module?
A module is a piece or part of something. We say something is modular if it comes in pieces or you can easily separate it into pieces. LEGO blocks might be the perfect example of something modular. You can take a bunch of different pieces and build many different things with them.

In Python, modules are smaller pieces of a bigger program. Each module, or piece, is a separate file on your hard drive. You can take a big program and split it up into more than one module, or file. Or you can go the other way—start with one small module and keep adding pieces to make a big program.

### Why use modules?
So why go to all the trouble of splitting our program up into smaller pieces, when we’re going to need them all to make the program work? Why not just leave everything in one big file? 

There are a few reasons:  
&emsp;&emsp;■ It makes the files smaller, which makes it easier to find things in your code.  
&emsp;&emsp;■ Once you create a module, you can use it in lots of programs. That saves you from starting all over again next time you need the same functions.  
&emsp;&emsp;■ You don’t always need to use all the modules together. Being modular means that you can use different combinations of the parts to do different jobs, just as you can make many different things out of the same set of LEGO blocks.

### Buckets of blocks
In the chapter about functions, we said that functions are like building blocks. You can think of a module as a bucket of building blocks. You can have as few or as many blocks in a bucket as you want, and you can have many different buckets. Maybe you have one bucket for all the square blocks, one for the flat pieces, and one for all the odd-shaped blocks. That’s usually how programmers use modules—they collect similar kinds of functions together in a module. Or they might collect all the functions they need for a project together in a module, just as you would gather all the blocks you need for a castle together in one bucket.

### How do we create modules?
Let’s create a module. A module is just a Python file, like the one in following code, and save it as **my_module.py**.
```python
# this is the file "my_module.py"
# we're going to use it in another program
def c_to_f(celsius):
    fahrenheit = celsius * 9.0 / 5 + 32
    return fahrenheit
```
That’s it! You have just created a module! Your module has one function in it, the `c_to_f()` function, which converts a temperature from Celsius to Fahrenheit.

Next, we’ll use **my_module.py** in another program. 

### How do we use modules?
In order to use something that is in a module, we first have to tell Python which modules we want to use. The Python keyword that lets you include other modules in your program is `import`. You use it like this:
```python
import my_module
```
Let’s write a program that uses the module we just wrote. We’re going to use the `c_to_f()` function to do a temperature conversion.

We already saw how to use a function and pass parameters (or arguments) to it. The only difference here is that the function will be in a separate file from our main program, so we’ll have to use `import`. The program in following uses the module we just wrote, **my_module.py**.  
```python
import my_module # my_module contains the c_to_f() function

celsius = float(input ("Enter a temperature in Celsius: "))
fahrenheit = c_to_f(celsius)
print("That's ", fahrenheit, " degrees Fahrenheit")
```
Create a new IDLE editor window, and type in this program. Save it as **modular.py**, and then run it to see what happens. You will need to save it in the same folder (or directory) as **my_module.py**.

Did it work? You should have seen something like this:
```python
>>> ============================ RESTART ============================
>>>
Enter a temperature in Celsius: 34
Traceback (most recent call last):
  File "C:/local_documents/Warren/PythonBook/Sample programs/modular.py", 
line 3, in -toplevel-
    fahrenheit = c_to_f(celsius)
NameError: name 'c_to_f' is not defined
```
It didn’t work! What happened? The error message says that the function `c_to_f()` isn’t defined. But we know it’s defined in `my_module`, and we did import that module.

The answer is that we have to be more specific in telling Python about functions that are defined in other modules. One way to fix the problem is to change the line
```python
fahrenheit = c_to_f(celsius)
```
to
```python
fahrenheit = my_module.c_to_f(celsius)
```
Now we’re specifically telling Python that the `c_to_f()` function is in the `my_module` module. Try the program with this change and see if it works.

### Namespaces
You can also import certain features from a module like
```python
>>> from time import sleep
```
or
```python
>>> from pygame import display
```
You see? You can use from to import certain parts of a module.
This is a bit of a complicated topic, but it’s something you need to know about, so now is a good time to talk about it.

#### What’s a namespace?
Imagine that you’re in Mr. Morton’s class at school, and there’s someone named Shawn in your class. Now imagine that, in another class in your school taught by Mrs. Wheeler, there’s another Shawn. If you’re in your own class and you say, “Shawn has a new backpack,” everyone in your class will know (or at least they’ll assume) that you mean the Shawn in your class. If you meant the other one, you’d say, “Shawn in Mrs. Wheeler’s class,” or “the other Shawn,” or something like that.

In your class, there’s only one Shawn, so when you say “Shawn,” your classmates know which person you’re talking about. To put this in another way, in the space of your class, there’s only one name “Shawn.” Your class is your namespace, and in that namespace, there’s only one Shawn, so there’s no confusion.
![](https://github.com/changemyheart/Pictures/blob/master/2017-09-27_193838.png?raw=true)
Now, if the principal has to call Shawn to the office over the public address system, she can’t just say, “Would Shawn please come to the office.” If she did that, both Shawns would show up at the office. For the principal using the public address system, the namespace is the whole school. That means everyone in the school is listening for the name, not just one class. So she has to be more specific about which Shawn she means. She would have to say something like, “Would Shawn from Mr. Morton’s class please come to the office.”
![](https://github.com/changemyheart/Pictures/blob/master/2017-09-27_193856.png?raw=true)
The other way the principal could get the correct Shawn is to go to the doorway of your class and say, “Shawn, would you please come with me.” There would be only one Shawn listening, and she would get the right one. In that case, the namespace would be just one classroom, not the whole school.
![](https://github.com/changemyheart/Pictures/blob/master/2017-09-27_193911.png?raw=true)
In general terms, programmers refer to smaller namespaces (like your classroom) as local namespaces and larger ones (like the whole school) as global namespaces.

#### Importing namespaces
Let’s assume that there’s nobody in your school, John Young School, named Fred. If the principal goes on the public address system and asks for Fred, she won’t get anyone. Now imagine that another school down the road, Stephen Leacock School, is having some repairs done, so one of their classes moves into a portable at your school. In that class, there’s a student named Fred. But that portable isn’t connected to the public address system yet. If the principal calls for Fred, she won’t get anybody. But if she connects the new portable to the public address system and then calls for Fred, she will get the Fred from Stephen Leacock School.

Connecting the portable from the other school is like importing a module in Python. When you import a module, you have access to all the names in that module: all the variables, all the functions, and all the objects.

Importing a module means the same thing as importing a namespace. When you import the module, you import the namespace.

There are two ways to import a namespace (or module). You can do it like this:
```python
import StephenLeacock
```
If you do it that way, `StephenLeacock` is still a separate namespace. You have access to the namespace, but you have to specify which namespace you want before you use it. So the principal would have to do something like this:
```python
call_to_office(StephenLeacock.Fred)
```
She would still have to give the namespace (`StephenLeacock`) as well as the name (`Fred`) if she wanted to reach Fred. That’s what we did a few pages ago with our temperature-con-version program. 

To make it work, we wrote this:
```python
fahrenheit = my_module.c_to_f(celsius)
```
We specified the namespace (`my_module`) as well as the name of the function (`c_to_f`).

The other way to import a namespace is like this:
```python
from StephenLeacock import Fred
```
If the principal does it that way, the name `Fred` from `StephenLeacock` gets included in her namespace, and she can reach Fred like this:
```python
call_to_office(Fred)
```
Because `Fred` is now in her namespace, she doesn’t have to go to the `StephenLeacock` namespace to get `Fred`.

In this example, the principal only imported one name, `Fred`, from `StephenLeacock` into her local namespace. If she wanted to import everyone, she could do this:
```python
from StephenLeacock import *
```
Here, the star (`*`) means all. But she has to be careful. If there are any students with the same names from Stephen Leacock School as there are from John Young School, there will be confusion.

#### Whew!
At this point, the whole namespace thing might still be a little fuzzy. Don’t worry! It’ll become clearer as we do examples in later chapters. Whenever we need to import modules, I’ll explain exactly what we’re doing.

### Standard modules
Now that we know how to create and use modules, do we always have to write our own modules? No! That’s one of the great things about Python.

Python comes with a bunch of standard modules to let you do things like find files, tell the time (or count time), or generate random numbers, among other things. Sometimes, people say Python has “batteries included,” and that’s what they’re talking about—all of Python’s standard modules. This is known as the Python Standard Library.

Why do these things have to be in separate modules? Well, they don’t have to be, but the people who designed Python decided that it would be more efficient. Otherwise, every Python program would have to include every possible function. This way, you just include the ones you need.

Of course, some things (like `for`, and `if-else`) are basic commands in Python, so you don’t need a separate module for them—they’re in the main part of Python.

If Python doesn’t have a module for something you want to do (like make a graphical game), there are other add-on modules that you can download, usually for free! We have included several of these with this book, and they were installed if you used the install program on the book’s web site. If not, you can always install them separately.

Let’s look at a couple of the standard modules.

#### Time
The `time` module lets you get information from your computer’s clock, like the date and the time. It also lets you add delays to your programs. (Sometimes the computer does things too quickly, and you have to slow it down.)

The `sleep()` function in the `time` module is used to add a delay—that is, to make the program wait and do nothing for a while. It’s like putting your program to sleep, which is why the function is called `sleep()`. You tell it how many seconds you want it to sleep.

The program in following demonstrates how the `sleep()` function works. Try typing, saving, and running it, and see what happens.
```python
import time
print("How", end='')
time.sleep(2)
print("are", end='')
time.sleep(2)
print("you", end='')
time.sleep(2)
print("today?")
```
Notice that, when we called the `sleep()` function, we had to put `time`. in front of it. That’s because, even though we `import`ed `time`, we didn’t make it part of the main program’s namespace. So every time we want to use the `sleep()` function, we have to call `time.sleep()`.

If we tried something like this,
```python
import time
sleep(5)
```
it wouldn’t work, because `sleep` isn’t in our namespace. We’d get an error message like this:
```python
NameError: name 'sleep' is not defined
```
But if you import it like this,
```python
from time import sleep
```
that tells Python, “Look for the variable (or function or object) named `sleep` in the `time` module, and include it in my namespace.” Now, we could use the `sleep` function without putting `time`. in front of it:
```python
from time import sleep
print('Hello, talk to you again in 5 seconds...')
sleep(5)
print('Hi again')
```
If we want the convenience of importing names into the local namespace (so we don’t have to specify the module name every time), but we don’t know which names in the module we’ll need, we can use the star (`*`) to import all names into our namespace:
```python
from time import *
```
The `*` means all, so this imports all the available names from the module. We have to be careful with this one. If we create a name in our program that is the same as one in the `time` module, there will be a conflict. Importing with `*` isn’t the best way to do it. It’s better to only import the parts that you need.

Remember the countdown program we made? Now you know what the line `time.sleep(1)` in that program was doing.

#### Random numbers
The `random` module is used for generating random numbers. This is very useful in games and simulations.

Let’s try using the random module in interactive mode:
```python
>>> import random
>>> print(random.randint(0, 100))
4
>>> print(random.randint(0, 100))
72
```
Each time you use `random.randint()`, you get a new, random integer. Because we passed the arguments 0 and 100 to it, the integer will be between 0 and 100. We used `random.randint()` in the number-guessing program in chapter 1 to create the secret number.

If you want a random decimal number, use `random.random()`. You don’t have to put anything between the brackets, because `random.random()` always gives you a number between 0 and 1.
```python
>>> print(random.random())
0.270985467261
>>> print(random.random())
0.569236541309
```
If you want a random number between, say, 0 and 10, you can just multiply the 
result by 10.
```python
>>> print(random.random() * 10)
3.61204895736
>>> print(random.random() * 10)
8.10985427783
```

---

## What did you learn?
In this chapter, you learned  
&emsp;&emsp;■ what a module is.  
&emsp;&emsp;■ how to create a module.  
&emsp;&emsp;■ how to use a module in another program.  
&emsp;&emsp;■ what namespaces are.  
&emsp;&emsp;■ what’s meant by local and global namespaces and variables.  
&emsp;&emsp;■ how to bring names from other modules into your namespace.

and you also saw a couple of examples of Python’s standard modules.

## Test your knowledge
1. What are some of the advantages of using modules?  
2. How do you create a module?  
3. What Python keyword do you use when you want to use a module?  
4. Importing a module is the same as importing a __________.  
5. What are two ways to import the `time` module so that you have access to all the names (that is, all the variables, functions, and objects) in that module?

## Try it out
1. Write a module that has the “print your name in big letters” function from the “Try it out” section in chapter 13. Then write a program that imports the module and calls the function.
2. Modify the code in listing 15.2 so that you bring `c_to_f()` into the main program’s namespace. That is, change it so you can write
```python
fahrenheit = c_to_f(celsius)
```
instead of
```python
fahrenheit = my_module.c_to_f(celsius)
```
3. Write a short program to generate a list of five random integer numbers from 1 to 20, and print them out.
4. Write a short program that prints out a random decimal number every 3 seconds for 30 seconds.
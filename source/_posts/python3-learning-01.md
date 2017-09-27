---
title: python3 learning 01
date: 2017-09-16 20:28:51
tags: python3
---
## lean python3 from now on.

In programming, `print` often means to display text on the screen, instead of printing it on a piece of paper using your printer.
```python
>>>print('Hello World!')
Hello World!
>>>
```
>`pront` is not equal to `print`
A keyword is a special word that is part of the Python language (also known as a reserved word).

```python
>>>print (3 + 3)
6
>>>print (5 * 9)
45
>>>
```
> Python can do addition and multiplication!
In pretty much all computer programs and languages, the `*` symbol is used
for multiplication. That character is called an asterisk or star.

---

```python
>>> print ("cat" + "dog")
catdog
>>>
```
or:
```python
>>> print ("Hello" * 20)
Hello Hello Hello Hello Hello Hello Hello Hello Hello Hello
Hello Hello Hello Hello Hello Hello Hello Hello Hello Hello
>>>
```
>Besides math, another thing computers are good at is doing things over and
over again. Here we told Python to print “Hello” twenty times. 

### Syntax errors

Syntax is the spelling and grammar rules for a programming language, so a syntax error means that you have typed something that is not proper Python code.

```python
print "Hello, and welcome to Python!"
print "I hope you will enjoy learning to program."
print Bye for now!"
```
>We missed a quote mark between `print` and `Bye for now!"`
If you tried to run this program, it would pop up a message saying “There’s an error in your program: `invalid syntax`.” Then you would have to look at your code to see what’s wrong.

### Runtime errors

>The second kind of error that can happen is one that Python (or IDLE) can’t detect before it runs the program. This kind of error only happens when the program runs, so it is called a runtime error. Here’s an example of a runtime error in a program:

```python
print ("Hello" + 5)
```

><font color=red>TypeError: cannot concatenate 'str' and 'int' objects.   
>
><font color=yellow-red>In Python, we can’t add different kinds of things together, like a number and some text. That’s why print "Bye for now!" + 5 gave us an error. It’s like saying, “If I take 5 apples and add 3 alligators, how many do I have?” we have 8, but 8 of what? Adding these together doesn’t really make sense. But we can multiply almost anything by a number to get more of that kind of thing. (If we have 2 alligators and we multiply by 5, we have 10 alligators!) That’s why print "Bye for now!" * 5 works. 

### Number-guessing game
```python
import random
secret = random.randint(1, 99)
guess = 0
tries = 0
print ("AHOY!  I'm the Dread Pirate Roberts, and I have a secret!")
print ("It is a number from 1 to 99.  I'll give you 6 tries. ")
while guess != secret and tries < 6:   
    guess = input("What's yer guess? ")
    if guess < secret:
        print ("Too low, ye scurvy dog!")
    elif guess > secret:
        print ("Too high, landlubber!")
    tries = tries + 1
if guess == secret:                        
    print ("Avast! Ye got it!  Found my secret, ye did!")
else:
    print ("No more guesses!  Better luck next time, matey!")
    print ("The secret number was", secret)
```

---

## Test your knowledge
1. How do you start IDLE?
2. What does print do?
3. What is the symbol for multiplication in Python?
4. What does IDLE display when you start to run a program?
5. What is another word for running a program?

## Try it out
1. In interactive mode, use Python to calculate the number of minutes in a week.
2. Write a short program to print three lines: your name, your birth date, and your favorite color. The output should look something like this:

>My name is Warren Sande.    
I was born January 1, 1970.
My favorite color is blue. 

Save the program and run it. If the program doesn’t do what you expect, or you getany error messages, try to fix it and make it work.

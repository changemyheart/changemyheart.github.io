---
title: python3 learning 08
date: 2017-09-21 19:11:32
tags: python3
---
## Just for You—Comments
Up until now, everything we have typed into our programs (and in interactive mode) has been instructions to the computer. But it’s a very good idea to include some notes to yourself in your programs, describing what the program does and how it works. This will help you (or someone else) look at your program later and figure out what you did. 

In a computer program, these notes are called comments.

### Adding comments
Comments are only for you to read, not for the computer to execute. Comments are part of the program’s documentation, and the computer ignores them when it runs your program. 

Python has a couple of ways to add comments to your program.
>Documentation is information about a program that describes the program and how it works. Comments are one part of a program’s documentation, but there may be other parts, outside the code itself, that describe things like  
&emsp;&emsp;· why the program was written (its purpose)  
&emsp;&emsp;· who wrote it  
&emsp;&emsp;· who it’s meant for (its audience)  
&emsp;&emsp;· how it’s organized  
and much more. Larger, more complicated programs usually have more documentation.

### Single-line comments
You can make any line into a comment by starting it with the “`#`” character. (This is called the number sign or sometimes the pound sign.)
```python
# This is a comment in a Python program
print('This is not a comment')
```
If you run these two lines, you’ll get the following output:  

    This is not a comment  
>The first line is ignored when the program runs. The comment, which starts with the # character, is only for you and other people reading the code.

### End-of-line comments
You can also put comments at the end of a line of code, like this:
```python
# This is a comment in a Python program
area = length * width    # Calculate the area of the rectangle
```
>The comment starts at the `#` character. Everything before the `#` is a normal line of code. Everything after that is a comment.

### Multiline comments
Sometimes you want to use more than one line for comments. You could use several lines with the # character at the start of each, like this:
```python
# ***************
# This is a program to illustrate how comments are used in Python
# The row of stars is used to visually separate the comments
# from the rest of the code
# ***************
```
Multiline comments are good for making sections of your code stand out visually when you’re reading it. You can use them to describe what’s going on in a section of code. A multiline comment at the start of a program could list the author’s name, the name of the program, the date it was written or updated, and any other information you think might be useful.

#### Triple-quoted strings
There is another way to make something that acts like a multiline comment in Python. You can just make a triple-quoted string with no name. So you can do this:
```python
""" Here is a comment that is on multiple
lines, using a triple-quoted string.
It's not really a comment, but it
behaves like one.
"""
```
Because the string has no name and the program isn’t “doing” anything with the string, it has no effect on the way the program runs. So it acts like a comment, even though it isn’t a comment in strict Python terms.

>Some Python programmers say that you shouldn’t use triple-quoted strings (multiline strings) as comments. Personally, I don’t see any good reason not to. The reason for comments is to make your code more readable and understandable. If you find that triple-quoted strings are convenient for you, it’s more likely you’ll put comments in your code, which is a good thing.

### Commenting style
So now you know how to add comments. But what kind of stuff should you put in them? 

Because they don’t affect how the program runs, we say that they’re a matter of “style.” That means you can put anything you want in your comments (or not use any at all). But it doesn’t mean comments are not important. Most programmers learn this the hard way, 

when they go back to a program they wrote several weeks, months, or years ago (or even one they wrote yesterday) and can’t understand it! That’s usually because they didn’t put in enough comments to explain how the program worked. It might seem obvious when you’re writing it, but it can be a complete mystery when you look at it later.

There are no hard-and-fast rules for what you should put in comments, but I encourage you to add as many comments as you like. For now, the more the better. It’s better to err on the side of too many comments than too few. As you get more experience with programming, you’ll get a feel for how much and what kind of commenting works best for you.

### Commenting out
You can also use comments to temporarily exclude parts of the program from running. Anything that is a comment will be ignored.
```python
#print "Hello"
print("World")
>>> =============== RESTART ================
>>> 
World
>>> 
```
>Because `print("Hello")` was commented out, that line was not executed, so the word “Hello” didn’t print. 

This is useful when you’re debugging a program and only want certain parts to run and other parts to be ignored. Just put a # in front of any line you want the computer to ignore, or put triple quotes around a section of code you want the computer to ignore.

---

## What did you learn?
In this chapter, you learned that  
&emsp;&emsp;■ comments are just for you (and other humans), not for the computer.  
&emsp;&emsp;■ comments can also be used to block out parts of the code, to prevent them from running.  
&emsp;&emsp;■ you can use triple-quoted strings as a kind of comment that spans multiple lines.

## Test your knowledge
Since comments are pretty simple, we’ll take a break and not have any test questions for this chapter.
---
title: python3 learning 04
date: 2017-09-19 19:18:00
tags: python3
---
## Types of Data
We have seen that there are at least three different types of things we can assign to a variable (to keep in the computer’s memory): integers, floating-point numbers, and strings. There are other types of data in Python, which we will learn about later, but for now these three will do. In this chapter, we’re going to learn how you can tell what type something is. We will also see how to make one type from another.  
<!-- more -->

### Changing types
Quite often we need to convert data from one type to another. For instance, when we want to print a number, it needs to be converted to text in order for the text to appear on the screen. Python’s print command can do that for us, but sometimes we need to convert without printing, or to convert from strings to numbers (which print can’t do). This is called type conversion. So how does it work?

Python doesn’t actually “convert” things from one type to another. It creates a new thing, of the type you want, from the original thing. Here are some functions that convert data from one type to another:  
&emsp;&emsp;■ `float()` will create a new float (decimal number) from a string or integer.   
&emsp;&emsp;■ `int()` will create a new integer from a string or float.  
&emsp;&emsp;■ `str()` will create a new string from a number (or any other type).

The parentheses at the end of `float()`, `int()`, and `str()` are there because they are not Python keywords, they are some of Python’s built-in functions. 

### Changing an int to a float
Let’s start with an integer and create a new floating-point number (decimal number) from it, using `float()`:
```python
>>> a = 24
>>> b = float(a)
>>> a
24
>>> b
24.0
```
>Notice that b got a decimal point and a 0 at the end. That tells us it is a float and not an integer. The variable a stayed the same, because `float()` doesn’t change the original value—it creates a new one.

### Changing a float to an int
Now let’s try the reverse—start with a decimal number and create an integer, using int():
```python
>>> c = 38.0
>>> d = int(c)
>>> c
38.0
>>> d
38
```
>We created a new integer, `d`, which is the whole number part of `c`.

Let’s try another one:
```python
>>> e = 54.99
>>> f = int(e)
>>> print e
54.99
>>> print f
54
```
>Even though 54.99 is very close to 55, you still get 54 for the integer. The `int()` function always rounds down. It doesn’t give you the nearest integer, it gives you the next lowest integer. The `int()` function basically chops off the decimal part. 

### Changing a string to a float
We can also create a number from a string, like this:
```python
>>> a = '76.3'
>>> b = float(a)
>>> a
'76.3'
>>> b
76.3
```

>Notice that, when we displayed `a`, the result had quotes around it. That’s Python’s way of telling us that `a` is a string. When we displayed `b`, we got the floating-point value with all the decimal places.

### Getting more information: type()
Python has another function, `type()`, which explicitly tells us the type of a variable.   
Let’s try it:
```python
>>> a = '44.2'
>>> b = 44.2
>>> type(a)
<type 'str'>
>>> type(b)
<type 'float'>
```
>The `type()` function told us that `a` is of `type 'str'`, which stands for string, and `b` is of `type 'float'`. No more guessing!

### Type-conversion errors
Of course, if you give int() or float() something that is not a number, it won’t work.   
Try it and see:
```python
>>> print float("fred")
Traceback (most recent call last):
  File "<pyshell#1>", line 1, in -toplevel-
    print float ("fred")
ValueError: invalid literal for float(): fred
```
>We got an error message. The invalid literal error message means that Python doesn’t know how to create a number from "fred". Do you?

### Using type conversions
Going back to your Fahrenheit to Celsius temperature-conversion program from the “Try it out” section in chapter 3, remember that you needed to fix the integer-division behavior to get the right answer, by changing the 5 to 5.0 or the 9 to 9.0:
```python
cel = 5.0 / 9 * (fahr – 32)
```
The `float()` function gives you another way of doing this:
```python
cel = float(5) / 9 * (fahr – 32)
```
or:
```python
cel = 5 / float(9) * (fahr – 32)
```

---

## What did you learn?
In this chapter, you learned about  
&emsp;&emsp;■ converting between types (or, more correctly, creating types from other types): `str()`, `int()`, and `float()`.  
&emsp;&emsp;■ checking the type of a variable using `type()`.

## Test your knowledge
1. When you use `int()` to convert a decimal number to an integer, does the result get rounded up or down?  
2. In your temperature-conversion program, would this have worked?  
&emsp;`cel = float(5 / 9 * (fahr – 32))`  
What about this:  
&emsp;`cel = 5 / 9 * float(fahr – 32)`  
If not, why not? 
3. (Extra challenging question) Without using any other functions besides `int()`, how could you get a number to round off instead of round down? (For example, 13.2 would round down to 13, but 13.7 would round up to 14.) 

## Try it out
1. Use `float()` to create a number from a string like `'12.34'`. Make sure the result is really a number!
2. Try using `int()` to create an integer from a decimal number like `56.78`. Did the answer get rounded up or down?
3. Try using `int()` to create an integer from a string. Make sure the result is really an integer!
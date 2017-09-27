---
title: python3 learning 03
date: 2017-09-18 20:20:43
tags: python3
---
## Basic Math
<!-- more -->

### The four basic operations
We already saw Python do a little math in chapter 1: addition, using the plus (`+`) sign, and multiplication, using the asterisk (`*`) sign.

Python uses the hyphen (-) (which is also called the minus sign) for subtraction, as you would expect:
```python
>>> print 8 – 5
3
```

Because computer keyboards don’t have a division (÷) symbol, all programs use the forward slash (`/`) for division.
```python
>>> print 6/2
3
```

Integers are the numbers you can easily count, like 1, 2, 3, as well as 0 and the negative numbers, like –1, –2, –3.

Decimal numbers (also called real numbers) are the numbers with a decimal point and some digits after it, like 1.25, 0.3752, and –101.2.

In computer programming, decimal numbers are also called floating-point numbers, or sometimes floats for short (or float for just one of them). This is because the decimal point “floats” around. You can have the number 0.00123456 or 12345.6 in a float.

If you enter either of the two numbers as a decimal number, Python knows 
you want the answer as a decimal number. 
```python
>>> print 3.0 / 2
1.5
```
### Operators
>The `+`, `-`, `*`, and `/` symbols are called operators. That’s because they “operate on,” or work with, the numbers we put around them. The `=` sign is also an operator, and it is called the assignment operator, because we use it to assign a value to a variable. 

#### Order of operations
```python
>>> print 2 + 3 * 4
14
```
>The order that Python uses is the same one you learned (or will learn) in math class. Exponents come first, then multiplication and division, and then addition and subtraction. 

If you want to change the order of operations and make something go first, you just put parentheses (round brackets) around it, like this:
```python
>>> print (2 + 3) * 4
20
```

### Two more operators
#### Exponentiation—raising to a power
If you wanted to multiply 3 by itself 5 times, you could write
```python
>>> print 3 * 3 * 3 * 3 * 3
243
```
But this is the same as 3 5 , or “three exponent five,” or “three to the power of five.” Python uses a double star (asterisk) for exponents or raising a number to a power.
```python
>>> print 3 ** 5
243
```

One reason for using an exponent instead of just multiplying several times is that it is easier to type. But a more important reason is that with ** you can have exponents that are not integers, like this:
```python
>>> print 3 ** 5.5
420.888346239
```
>There is no easy way to do that using just multiplication.

#### Modulus—getting the remainder
Python has a special operator for calculating the remainder for integer division. It is called the modulus operator, and the symbol is the percent symbol (`%`). You use it like this:
```python
>>> print 7 % 2
1
```
#### Increment and decrement
Remember the example from the last chapter: `score = score + 1`? We said that was called incrementing. A similar thing is `score = score - 1`, which is called decrementing. These are done so often in programming that they have their own operators: `+=` (increment) and `-=` (decrement).
```python
>>> number = 7
>>> number += 1
>>> print (number)
8
```
or:
```python
>>> number = 7
>>> number -= 1
>>> print (number)
6
```
>The first one adds one to the number. (It changes from 7 to 8.) The second one subtracts one from the number. (It changes from 7 to 6.)

### Really  big  and really  small
Try this in interactive mode:
```python
>>> print 9938712345656.34 * 4823459023067.456
4.79389717413e+025
>>>
```
>(It doesn’t matter exactly what numbers you type in—any big numbers with decimals will do.)

The e is one way of displaying really big or really small numbers on a computer. It’s called E-notation. When we’re working with really big (or really small) numbers, showing all the digits and decimal places can be kind of a pain. These kinds of numbers show up a lot in math and science. 

For example, if an astronomy program was displaying the number of kilometers from Earth to the star Alpha Centauri, it could show 38000000000000000 or 38,000,000,000,000,000 or 38 000 000 000 000 000. (That’s 38 quintillion kilometers!) But either way, you would get tired of counting all those zeros. 

Another way to display this number is to use scientific notation, which uses powers of 10 along with decimal numbers. In scientific notation, the distance to Alpha Centauri would be written like this: 3.8 x 10 16 . (See how the 16 is raised above the line, and is smaller?) This reads as “three point eight times ten to the power of sixteen” or “three point eight times ten to the sixteenth.” What it means is you take 3.8 and move the decimal point sixteen places to the right, adding zeros as needed. 

![uppercase](https://github.com/changemyheart/Pictures/blob/master/uppercase.png?raw=true)
Scientific notation is great if you can write the 16 as an exponent, raised above the line and smaller, like we did here. If you are working with pencil and paper, or a program that supports superscripts, then you can use scientific notation. 
>Superscript means a character or characters that are raised above the rest of the text, like this: 10^13 . The 13 here is the superscript. Usually, superscripts are also smaller than the main text. 

#### E-notation
In E-notation, our number would be 3.8E16 or 3.8e16. This reads as “three point eight exponent sixteen” or “three point eight e sixteen” for short. It is assumed that the exponent is a power of 10. That’s the same as writing 3.8x10^16

For very small numbers, like 0.0000000000001752, a negative exponent is used. The scien-tific notation would be 1.752x10 -13 , and the E-notation would be 1.752e-13. A negative exponent means to move the decimal place to the left instead of the right.
![lowercase](https://github.com/changemyheart/Pictures/blob/master/lowercase.png?raw=true)
You can use E-notation to enter very big and very small numbers (or any number, for that matter) into Python. Later we will see how to make Python print numbers using E-notation.

Try entering some numbers in E-notation:
```python
>>> a = 2.5e6
>>> b = 1.2e7
>>> print (a + b)
14500000.0
>>>
```
Although we entered the numbers in E-notation, the answer came out as a regular decimal number. That’s because Python won’t display numbers in E-notation unless you specifically tell it to, or the numbers are really big or really small (lots of zeros).   
Try this:
```python
>>> c = 2.6e75
>>> d = 1.2e74
>>> print c + d
2.72e+075
>>>
```
>This time, Python displayed the answer in E-notation automatically, because it wouldn’t make sense to display a number with 73 zeros!

#### Exponents vs. E-notation
Don’t get confused between raising a number to a power (also called exponentiation) and E-notation. 

* 3**5 means 3^5 , or “three to the fifth power” or 3 * 3 * 3 * 3 * 3, which is equal to 243.   
* 3e5 means 3 * 10^5  or “three times ten to the fifth power,” or 3 * 10 * 10 * 10 * 10 *10, which is equal to 300,000.

Raising to a power means you are raising the number itself to that power. E-notation means you are multiplying by a power of 10. 

Some people would read both 3e5 and 3**5 as “three exponent five,” but they are two different things. It doesn’t matter so much how you say it, as long as you understand what each one means.

---

## What did you learn?
* how to do basic math operations in Python.
* about integers and floats.
* about exponentiation (raising numbers to a power).
* how to calculate the modulus (the remainder).
* all about E-notation.   

## Test your knowledge
1. What symbol does Python use for multiplication?
2. What answer would Python give for 8 / 3?
3. How would you get the remainder for 8 / 3?
4. How would you get the decimal answer for 8 / 3?
5. What’s another way of calculating 6 * 6 * 6 * 6 in Python?
6. How would you write 17,000,000 in E-notation?
7. What would 4.56e-5 look like in regular notation (not E-notation)?

## Try it out

1. Solve the following problems either using interactive mode or by writing a small program:
    a) Three people ate dinner at a restaurant and want to split the bill. The total is $35.27,and they want to leave a 15 percent tip. How much should each person pay? 
    b) Calculate the area and perimeter of a rectangular room, 12.5 meters by 16.7 meters.  
2. Write a program to convert temperatures from Fahrenheit to Celsius. The formula for that is: C = 5 / 9 * (F - 32). (Hint: Watch out for the integer-division gotcha!)  
3. Do you know how to figure out how long it will take to get somewhere in a car? The formula (in words) is “travel time equals distance divided by speed.” Make a program to calculate the time it will take to drive 200 km at 80 km per hour and display the answer.

---
title: python3 learning 05
date: 2017-09-19 19:48:18
tags: python3
---
## Input
What if you want to have the user enter any temperature she wants when the program runs? We said before that a program has three components: input, processing, and output. Our first program had only output. The temperature-conversion program had some processing (converting the temperature) and some output, but no input. It’s time to add the third ingredient to our programs: input. Input means getting something, some kind of information, into a program while it is running. 
<!-- more -->

That way we can write programs that interact with the user, which will make things a lot more interesting.

Python3 has a built-in function, called `input()`, that is used to get input from the user.

### input()
The `input()` function gets a string from the user. The normal way it gets this is from the keyboard—the user types in the input.

`input()` is another one of Python’s built-in functions, like `str()`, `int()`, `float()`, and `type()`. We’ll learn a lot more about functions later. But for now, you just need to remember to include the parentheses (round brackets) when you use `input()`. 

Here is how you use it:
```python
someName = input()
```
>This will let the user type in a string and assign it the name `someName`. 

Now let’s put this into a program.
```python
print ("Enter your name: ")
somebody = input()
print ("Hi", somebody, "how are you today?")
```
Save and run this program in IDLE to see how it works. You should see something like this: 
```python
Enter your name:
Warren
Hi Warren how are you today?
```
>I typed in my name, and the program assigned it the name `somebody`. 

#### A shortcut for raw_input() prompts
There is a shortcut for printing prompt messages. The `input()` function can print the message for you, so you don’t have to use a `print` statement:
```python
someName = raw_input ("Enter your name: ")
```
>It is like the `input()` function has print built in. We will use that shortcut from now on.

### Inputting numbers
We can use the `int()` or `float()` functions to create a number from the string that `input()` gives us. It would look like this:
```python
temp_string = input() 
fahrenheit = float(temp_string)
```
We got the user’s input as a string, using `input()`. Then we made a number from that, using `float()`. Once we had the temperature as a float, we gave it the name fahrenheit. 

But there is a little shortcut. We can do it all in one step, like this:
```python
fahrenheit = float(raw_input())
```
>This does exactly the same thing. It gets the string from the user and then creates a number from it. It just does it with a bit less code. 

### Using `int()` with `input()`
If the number you want the user to enter will always be an integer (no decimals), you can convert it with `int()`, like this:
```python
response = input("How many students are in your class: ")
numberOfStudents = int(response)
```


### Input from the Web
Usually, you get input for a program from the user. But there are other ways to get input, too. You can get it from a file on your computer’s hard drive or you can get it from the Internet.

If you have an Internet connection, you can try the program following code. It opens a file from the book’s web site and shows you the message that is in that file.
```python
import urllib
file = urllib.urlopen('http://helloworldbook.com/data/message.txt')
message = file.read() 
print (message)
```
>That’s it. With just four lines of code, your computer reaches across the Web to get a file from the book’s web site and display it. If you try this program (assuming you have a working Internet connection), you will see the message.

---

## What did you learn?
In this chapter, you learned about  
&emsp;&emsp;■ inputting text with `input()`.  
&emsp;&emsp;■ adding a prompt message to `input()`.  
&emsp;&emsp;■ inputting numbers using `int()` and `float()` with `input()`.  

## Test your knowledge
1. With this code,  
```python
answer = input()
```
&emsp;&emsp;if the user types in `12`, what type of data is `answer`? Is it a string or a number?  
&emsp;&emsp;2. How do you get `input()` to print a prompt message?  
&emsp;&emsp;3. How do you get an integer using `input()`?  
&emsp;&emsp;How do you get a float (decimal number) using `input()`?

## Try it out
1. In interactive mode, make two variables, one for your first name and one for your last name. Then, using a single print statement, print your first and last names together.
2. Write a program that asks for your first name, then asks for your last name, and then prints a message with your first and last names in it.
3. Write a program that asks for the dimensions (in feet) of a rectangular room, and then calculates and displays the total amount of carpet needed to cover the room.
4. Write a program that does the same as in #3, but that also asks for the cost per square yard of carpet. Then have the program display these three things:  
&emsp;&emsp;■ the total amount of carpet, in square feet.  
&emsp;&emsp;■ the total amount of carpet, in square yards (1 square yard = 9 square feet).  
&emsp;&emsp;■ the total cost of the carpet.  
5. Write a program that helps the user add up her change. The program should ask  
&emsp;&emsp;■ “How many quarters?”  
&emsp;&emsp;■ “How many dimes?”  
&emsp;&emsp;■ “How many nickels?”  
&emsp;&emsp;■ “How many pennies?”  
&emsp;&emsp;Then it should give the total value of the change.
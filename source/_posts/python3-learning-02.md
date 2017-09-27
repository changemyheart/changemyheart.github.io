---
title: python3 learning 02
date: 2017-09-17 20:23:42
tags: python3
---
## Names 
<!-- more -->
  
```python
>>>Teacher = "Mr. Morton"
>>>print (Teacher)
```
>You just created a thing that is made up of the letters 
“Mr. Morton”, and you gave it the name `Teacher`.       
>The equal sign (`=`) tells Python to assign or “make equal 
to.” You assigned the name `Teacher` to the series of let-
ters “Mr. Morton”. 

When you assign a value to a name (like assigning the value “Mr. Morton” to Teacher), it is stored in memory and is called a `variable`. In most programming languages, we say you store a value in a variable.
But Python does things a little differently from most other computer languages. Instead of storing values in variables, it’s more like putting names on values.

Let’s try that one with variables: 
```python
>>> First = 5
>>> Second = 3
>>> print (First + Second)
8
```
>Here, we created two names, `First` and `Second`. The number 5 was assigned to `First`, and the number 3 was assigned to `Second`. Then we printed the sum of the two. 

There’s another way to do this. Try this:
```python
>>> Third = First + Second
>>> Third
8
```
>Notice what we did here. In interactive mode, we can display the value of a 
variable just by typing its name, without using `print`. (This doesn’t work 
in a program.)

You can have more than one name for the same thing. Try this in interactive mode:
```python
>>> a = "Apple"
>>> b = a
>>> a
"Apple"
>>> b
"Apple"
```
>This is like sticking two tags on the same thing. One tag says `a` and one tag says `b`, but they are both stuck on “Apple”.

### What’s in a name?

You can call a variable anything you want (well, almost). The name can be as long as you want, and it can have letters and numbers in it, as well as the underscore character (`_`). 

But there are a few rules about variable names. The most important one is that they are case-sensitive, which means that uppercase and lowercase matter. So, `teacher` and `TEACHER` are two different names. So are `first` and `First`.

Another rule is that a variable name has to start with a letter or the underscore character. 

It can’t start with a number. So `4fun` is not allowed.

One more rule is that a variable name can’t have any spaces in it.

### Numbers and strings
A character, or series of characters (letters, numbers, or punctuation), is called a `string`. The way you tell Python that you are making a string is to put quotes around the characters. Python is not too fussy about whether you use single or double quotes. 

Either of these will work:
```python
>>> teacher = "Mr. Morton"
>>> teacher = 'Mr. Morton'
```

#### Concatenate
It’s not really correct to say “added” when talking about strings (like we just did). When you put characters or strings together to make a longer string, there is a special name for it. Instead of “adding” (which is only 
for numbers), it is called concatenation. This sounds like kon-kat-en-ay-shun. 
We say that you `concatenate` two strings.

#### Long strings
If you want to have a string that spans more than one line, you have to use a special kind of string called a triple-quoted string. Here is what it looks like:
```python
long_string = """Sing a song of sixpence, a pocket full of rye,
Four and twenty black birds baked in a pie.
When the pie was opened the birds began to sing.
Wasn't that a dainty dish to set before the king?"""
```
This kind of string starts and ends with three quote marks. The quote marks can be double or single quotes, so you could also do it this way:
```python
long_string = '''Sing a song of sixpence, a pocket full of rye,
Four and twenty black birds baked in a pie.
When the pie was opened the birds began to sing.
Wasn't that a dainty dish to set before the king?'''
```
>Triple-quoted strings can be very useful when you have several lines of text that you want to display together, and you don’t want to use a separate string for each line.

### How “variable” are they?
Variables are called “variables” for a reason. It’s because they are . . . well . . . variable! That means you can vary, or change, the value that is assigned to them. In Python, you do this by creating a new thing that is different from the old thing, and sticking the old label (the name) on the new thing. 

>Remember that things can have more than one name (more than one tag stuck on them).

### The new me
You can also make a variable equal to itself:
```python
>>> Score = 7
>>> Score = Score
```

I bet you’re thinking, “Well, that’s pretty useless!” And you’d be right. It’s kind of like saying “I am me.” But with a small change, you can become a whole new you! Try this:
```python
>>> Score = Score + 1
>>> print (Score)
8
```
>What happened here? In the first line, the `Score` tag was stuck on the value 7. We made a new thing, which was `Score + 1`, or 7 + 1. That new thing is 8. Then we took the `Score` tag off the old thing (7) and stuck it on the new thing (8). So `Score` has been reassigned from 7 to 8. 

>Whenever we make a variable equal something, the variable always appears on the left side of the equal sign (`=`). The trick is that the variable can also appear on the right. This turns out to be quite useful, and you’ll see it in a lot of programs. The most common use is to increment a variable (increase it by a certain amount), like we just did, or the opposite, to decrement a variable (decrease it by a certain amount). 

---

## What did you learn?
In this chapter, you learned

- how to “remember” or keep things in the computer’s memory using variables.
- that variables are also called “names” or “variable names.”
- that variables can be different kinds of things, such as numbers and strings.

## Test your knowledge
1. How do you tell Python that a variable is a string (characters) instead of a number?
2. Once you have created a variable, can you change the value that is assigned to it?
3. With variable names, is `TEACHER` the same as `TEACHEr`?
4. Is '`Blah`' the same as "`Blah`" to Python?
5. Is `'4'` the same as 4 to Python?
6. Which of the following is not a correct variable name? Why?
    a) `Teacher2`
    b) `2Teacher`
    c) `teacher_25`
    d) `TeaCher`
7. Is "10" a number or a string?

## Try it out
1. Make a variable and assign a number to it (any number you like). Then display your variable using `print`.

2. Modify your variable, either by replacing the old value with a new value, or by adding something to the old value. Display the new value using `print`.

3. Make another variable and assign a string (some text) to it. Then display it using `print`.

4. Just like in the last chapter, in interactive mode, get Python to calculate the number of minutes in a week. But this time, use variables. Make a variable for `DaysPerWeek`, `HoursPerDay`, and `MinutesPerHour` (or make up your own names), and then multiply them together.

5. People are always saying there’s not enough time to get everything done. How many minutes would there be in a week if there were 26 hours in a day? (Hint: Change the `HoursPerDay` variable.)
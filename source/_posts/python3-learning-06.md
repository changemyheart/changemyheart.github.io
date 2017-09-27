---
title: python3 learning 06
date: 2017-09-20 19:28:01
tags: python3
---
## Decisions
If a program did the same thing every time, it would be a little boring and not very useful. Programs need to be able to make decisions on what to do. We’re going to add some different decision-making techniques to our processing repertoire.
<!-- more -->

### Testing
Programs need to be able to do different things based on their input. Here are a few examples:   
&emsp;&emsp;■ If Tim got the right answer, add 1 point to his score.  
&emsp;&emsp;■ If Jane hit the alien, make an explosion sound.  
&emsp;&emsp;■ If the file isn’t there, display an error message.

To make decisions, programs check (do a test) to see if a certain condition is true or not. In the first example above, the condition is “got the right answer.”

Python has only a few ways to test something, and there are only two possible answers for each test: true or false.

Here are some questions Python can ask to test something:  
&emsp;&emsp;■ Are two things equal?  
&emsp;&emsp;■ Is one thing less than another?  
&emsp;&emsp;■ Is one thing greater than another?

But wait a minute, “got the right answer” isn’t one of the tests we can do, at least not directly. That means we need to describe the test in a way Python can understand.

>Doing tests and making decisions based on the results is called branching. The program decides which way to go, or which branch to follow, based on the result of the test.

Python uses the keyword `if` to test conditions, like this:
```python
if timsAnswer == correctAnswer:
    print "You got it right!"  #These lines form a “block” of code because they’re 
    score = score + 1          #indented from the lines above and below
print "Thanks for playing."
```
>A block of code is one or more lines of code that are grouped together. They’re all related to a particular part of the program (like an `if` statement). In Python, blocks of code are formed by indenting the lines of code in the block.

The colon at the end of the `if` line tells Python that a block of instructions is coming next. The block includes every line that is indented from the `if` line, up until the next line that is not indented. 
>Indenting means that a line of code is pushed over to the right a bit. Instead of starting at the far left, it has some spaces at the beginning, so it starts a few characters away from the left side.

If the condition is true, everything in the following block will be done. In the previous short example, the second and third lines make up the block of statements for the `if` in the first line.

### Indenting
In some languages, indenting is just a matter of style—you can indent however you like (or not at all). But in Python, indenting is a necessary part of how you write the code. Indenting tells Python where blocks of code start and where they end.

Some statements in Python, like the `if` statement, need a block of code to tell them what to do. In the case of the `if` statement, the block tells Python what to do if the condition is true.

It doesn’t matter how far you indent the block, as long as the whole block is indented the same amount. A convention in Python is to use four spaces to indent blocks of code. It would be a good idea to follow this style in your programs.
>A convention just means lots of people do it that way.

### Am I seeing double?
Are there actually two equal signs in that if statement (`if timsAnswer == correctAnswer`)? Yes, there are, and here’s why.

People say, “Five plus four is equal to nine,” and they ask, “Is five plus four equal to nine?” One is a statement; the other is a question. 

In Python we have the same kinds of things—statements and questions. A statement might assign a value to a variable. A question might check if a variable is equal to a certain value. One means you’re setting something (assigning it or making it equal). The other means you’re checking or testing something (is it equal, yes or no?). So Python uses two different symbols.

We already saw the equal sign (`=`) used for setting or assigning values to variables. Here are a few more examples:
```python
correctAnswer = 5 + 3
temperature = 35
name = "Bill"
```

For testing whether two things are equal, Python uses a double equal sign (`==`), like this:
```python
if myAnswer == correctAnswer:
if temperature == 40:
if name == "Fred":
```

Testing or checking is also called comparing. The double equal sign is called a comparison operator. Remember, we talked about operators before. An operator is a special symbol that operates on the values around it. In this case, the operation is to test whether the values are equal.

### Other kinds of tests
Lucky for us, the other comparison operators are easier to remember: less than (`<`), greater than (`>`), and not equal to (`!=`). (You can also use `<>` for not equal to, but most people use `!=`.) You can also combine `>` or `<` with `=` to make greater than or equal to (`>=`) and less than or equal to (`<=`). You might have seen some of these in math class.

You can also “chain” two greater-than and less-than operators together to make an in-between test, like this:
```python
if 8 < age < 12:
```

This will check if the variable `age` has a value between, but not including, 8 and 12. This would be true if `age` was equal to 9, 10, or 11 (or 8.1 or 11.6, and so on). If we wanted to include the ages 8 and 12, we’d do this instead:
```python
if 8 <= age <= 12:
```
>Comparison operators are also called relational operators (because they test the relation between the two sides: equal or not equal, greater than or less than). A comparison is also called a conditional test or logical test. In programming, logical refers to something where the answer is either true or false.

### What happens if the test is false?
We’ve seen how to make Python do something if the result of a test is true. But what does it do if the test is false? In Python, there are three possibilities:  
&emsp;&emsp;■ Do another test. If the first test comes out false, you can get Python to test something else with the keyword `elif`, (which is short for “else if”) like this:
```python
if answer >= 10:
    print ("You got at least 10!")
elif answer >= 5:
    print ("You got at least 5!")
elif answer >= 3:
    print ("You got at least 3!")
```
&emsp;&emsp;You can have as many elif statements as you want after the if.  
&emsp;&emsp;■ Do something else if all the other tests come out false. You do this with the else keyword. This always goes at the end, after you’ve done the if and any elif statements:
```python
if answer >= 10:
    print ("You got at least 10!")
elif answer >= 5:
    print ("You got at least 5!")
elif answer >= 3:
    print ("You got at least 3!")
else:
    print ("You got less than 3.")
```
&emsp;&emsp;■ Move on. If you don’t put anything else after the `if` block, the program will continue on to the next line of code (if there is one) or it’ll end (if there is no more code).


Try making a program with the code above by adding a line at the beginning to input a number:
```python
answer = float(raw_input ("Enter a number from 1 to 15"))
```

### Testing for more than one condition
What if we want to test for more than one thing? Let’s say you made a game that was for eight-year-olds and up, and you want to make sure the player is in at least third grade. There are two conditions to meet. Here is one way you could test for both conditions:
```python
age = float(raw_input("Enter your age: "))
grade = int(raw_input("Enter your grade: "))
if age >= 8:
    if grade >= 3:
        print ("You can play this game.")
else:
    print ("Sorry, you can’t play the game.")
```
Notice that the first `print` line is indented eight spaces, not just four spaces. That’s because each `if` needs its own block, so each one has its own indenting.

#### Using “and”
That last example will work fine. But there is a shorter way to do the same thing. You can combine conditions like this:
```python
age = float(input("Enter your age: "))
grade = int(input("Enter your grade: "))
if age >= 8 and grade >= 3:         
    print "You can play this game."
else:
    print "Sorry, you can’t play the game."
```
>We combined the two conditions using the `and` keyword. The `and` means that both of the conditions have to be true for the following block to execute.

You can put more than two conditions together with `and`: 
```python
age = float(input("Enter your age: "))
grade = int(input("Enter your grade: "))
color = input("Enter your favorite color: ")
if age >= 8 and grade >= 3 and color == "green":
    print ("You are allowed to play this game.")
else:
    print ("Sorry, you can’t play the game.")
```
>If there are more than two conditions, all the conditions have to be true for the `if` statement to be true. 

There are other ways of combining conditions too. 

#### Using “or”
The `or` keyword is also used to put conditions together. If you use `or`, the block is executed if any of the conditions are true. 
```python
color = input("Enter your favorite color: ")
if color == "red" or color == "blue" or color == "green":
    print ("You are allowed to play this game.")
else:
    print ("Sorry, you can’t play the game.")
```
#### Using “not”
You can also flip around a comparison to mean the opposite, using `not`.
```python
age = float(input("Enter your age: "))
if not (age < 8):
    print ("You are allowed to play this game.")
else:
    print ("Sorry, you can’t play the game.")
```
>This line 
```python
if not (age < 8):
```
>means the same as this one:
```python
if age >= 8:
```

In both cases, the block executes if the age is 8 or higher, and it doesn’t if the age is lower than 8.

we saw math operators like `+`, `-`, `*`, and `/` before.  In this chapter, we saw the comparison operators `<`, `>`, `==`, and so on. The and, or, and not keywords are also operators. They’re called logical operators. They’re used to modify comparisons by combining two or more of them (`and`, `or`) or reversing them (`not`).

### Following table lists all the operators we’ve talked about so far.

Operator   Name                      What it does
--------- ------------------------- -------------------------------------------
=          Assignment                Assigns a value to a name (variable).
+          Addition                  Adds two numbers together. This can also be used to concatenate strings.
-          Subtraction               Subtracts two numbers.
+=         Increment                 Adds one to a number.
-=         Decrement                 Subtracts one from a number.
*          Multiplication            Multiplies two numbers together.
/          Division                  Divides two numbers. If both numbers are integers, the result will be just the integer quotient, with no remainder.
%          Modulus                   Gets the remainder (or modulus) for integer division of two numbers.
**         Exponentiation            Raises a number to a power. Both the number and the power can be integers or floats.
==         Equality                  Checks whether two things are equal.
<          Less than                 Checks whether the first number is less than the second number.
>          Greater than              Checks whether the first number is greater than the second num-ber.
<=         Less than or equal to     Checks whether the first number is less than or equal to the second number.
>=         Greater than or equal to  Checks whether the first number is greater than or equal to the second number.
!=&emsp;<> Not equal to              Checks whether two things are not equal. (Either operator can be used.)
--------- ------------------------- -------------------------------------------

---

## What did you learn?
In this chapter, you learned about   
&emsp;&emsp;■ comparison tests and the relational operators.  
&emsp;&emsp;■ indenting and blocks of code.  
&emsp;&emsp;■ combining tests using and and or.  
&emsp;&emsp;■ reversing a test using not.

## Test your knowledge
1. What will the output be when this program is run:
```python
my_number = 7
if my_number < 20:
    print ('Under 20')
else:
    print ('20 or over')
```
2. From the program in the first question, what will the output be if you change `my_number` to `25`?  
3. What kind of `if` statement would you use to check if a number was greater than 30 but less than or equal to 40?  
4. What kind of `if` statement would you use to check if the user entered the letter “Q” in either uppercase or lowercase? 

## Try it out 
1. A store is having a sale. They’re giving 10 percent off purchases of $10 or lower, and 20 percent off purchases of greater than $10. Write a program that asks the purchase price and displays the discount (10% or 20%) and the final price.  
2. A soccer team is looking for girls from ages 10 to 12 to play on their team. Write a program to ask the user’s age and if male or female (using “m” or “f”). Display a message indicating whether the person is eligible to play on the team.Bonus: Make the program so that it doesn’t ask for the age unless the user is a girl.  
3. You’re on a long car trip and arrive at a gas station. It’s 200 km to the next station. Write a program to figure out if you need to buy gas here, or if you can wait for the next station.  
The program should ask these questions:  
&emsp;&emsp;■ How big is your tank, in liters?  
&emsp;&emsp;■ How full is your tank (in percent—for example, half full = 50)?  
&emsp;&emsp;■ How many km per liter does your car get?  
&emsp;&emsp;The output should look something like this:

>&emsp;&emsp;Size of tank:  60  
&emsp;&emsp;percent full:  40  
&emsp;&emsp;km per liter:  10  
&emsp;&emsp;You can go another 240 km  
&emsp;&emsp;The next gas station is 200 km away  
&emsp;&emsp;You can wait for the next station.

or:

>&emsp;&emsp;Size of tank:  60  
&emsp;&emsp;percent full:  30  
&emsp;&emsp;km per liter:  8  
&emsp;&emsp;You can go another 144 km  
&emsp;&emsp;The next gas station is 200 km away  
&emsp;&emsp;Get gas now!

Bonus: Include a 5 liter buffer in your program, in case the fuel gauge isn’t accurate.  
4. Make a program where the user has to enter a secret password to use the program. You’ll know the password, of course (because it’ll be in your code). But your friends will either have to ask you, guess the password, or learn enough Python to look at the code and figure it out!  
The program can be anything you want, including one you have already written, or just a simple one that displays a message like “You’re in!” when he enters the right password.







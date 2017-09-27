---
title: python3 learning 07
date: 2017-09-20 20:42:23
tags: python3
---
## Loop the Loop
For most people, doing the same thing over and over again is very boring, so why not let the computer do that for us? Computers never get bored, so they’re great at doing repetitive tasks. In this chapter, we’re going to see how to make the computer repeat things.

Computer programs often repeat the same steps over and over again. This is called looping.   
There are two main kinds of loops:  
&emsp;&emsp;■ those that repeat a certain number of times—these are called counting loops  
&emsp;&emsp;■ those that repeat until a certain thing happens—these are called conditional loops   
because they keep going as long as some condition is true

### Counting loops
The first kind of loop is called a counting loop. You’ll also hear it called a for loop, because many languages, including Python, use the `for` keyword to create this kind of loop in a program. 

Let’s try a program that uses a counting loop.
```python
for looper in [1, 2, 3, 4, 5]:
    print("hello")
```

You should see something like this:
```python
>>> ================ RESTART ================
>>> 
hello
hello
hello
hello
hello
>>>
```

Hey, is there an echo in here? The program printed “hello” five times, even though there was only one `print` statement. How? The first line (`for looper in [1, 2, 3, 4, 5]:`) translated into plain English means this:

1. looper will start with the value 1 (so looper = 1).  
2. The loop will do whatever is in the next block of instructions one time for each value in the list. (The list is those numbers in square brackets.)  
3. Each time through the loop, the variable looper is assigned the next value in the list.

The second line (`print ("hello")`) is the block of code that Python will executeeach time around the loop. A `for` loop needs a block of code to tell the program what to do in each loop. That block (the indented part of the code) is called the body of the loop. (Remember, we talked about indenting and blocks in the last chapter.) 
>Each time through the loop is called an iteration.

Let’s try something else. Instead of printing the same thing every time, let’s make it print something different every time through the loop.
```python
for looper in [1, 2, 3, 4, 5]:
    print (looper)
```
The results should look like this:
```python
>>> ================ RESTART ================
>>> 
1
2
3
4
5
>>> 
```
This time, instead of printing “hello” five times, it printed the value of the variable `looper`. Each time through the loop, `looper` takes the next value in the list.

#### What are the square brackets for?
You might have noticed that our list of loop values is enclosed in square brackets. The square brackets and the commas between the numbers are the way you make a list in Python. We’ll learn more about lists soon. But for now, just know that a list is a kind of “container” for storing a bunch of things together. In this case, the things are numbers—the values that `looper` takes as it goes through different iterations of the loop. 

### Using a counting loop
Now let’s do something a bit more useful with loops. Let’s print a multiplication table. It only takes a small change to our program.
```python
for looper in [1, 2, 3, 4, 5]:
    print(looper, "times 8 =", looper * 8) 
```
You should see something like this:

Now we’re starting to see the power of loops. Without loops, we’d have had to write a program like this one to get the same result:
```python
print("1 times 8 =", 1 * 8)
print("2 times 8 =", 2 * 8)
print("3 times 8 =", 3 * 8)
print("4 times 8 =", 4 * 8)
print("5 times 8 =", 5 * 8)
```
To make a longer multiplication table (say, up to 10 or 20), this program would be a lot longer, but our loop program would be almost the same (just with more numbers in the list). Loops make this much easier!

### A shortcut—range()
In the previous example, we only looped 5 times:
```python
for looper  in [1, 2, 3, 4, 5]:
```
>But what if we wanted the loop to run 100 times, or 1000 times? That would be a lot of typing!

Luckily, there’s a shortcut. The `range()` function lets you just enter the starting and ending values, and it creates all the values in between for you. `range()` creates a list containing a range of numbers.

Let’s use the range() function in our multiplication table example.

You should see something like this:
```python
>>> ================= RESTART =================
>>> 
1 times 8 = 8
2 times 8 = 16
3 times 8 = 24
4 times 8 = 32
```
>It’s almost the same as the first one . . . except that it missed the last loop! Why?

The answer is that `range(1, 5)` gives us the list`[1, 2, 3, 4]`. You can try this in interactive mode:
```python
>>> print(range(1, 5))
[1, 2, 3, 4]
```
Why not 5?  
Well, that’s just the way the `range()` function works. It gives you a list of numbers starting at the first number and ending just before the last number. You need to take that into account and adjust the range to get the number of loops you want.

Following shows our program modified to give us the 8 times table up to 10.
```python
for looper in range(1, 11):
    print(looper, "times 8 =", looper * 8)
```
And here’s what we get when we run it:
```python
>>> ================== RESTART ==================
>>> 
1 times 8 = 8
2 times 8 = 16
3 times 8 = 24
4 times 8 = 32
5 times 8 = 40
6 times 8 = 48
7 times 8 = 56
8 times 8 = 64
9 times 8 = 72
10 times 8 = 80
```
In the above program, `range(1, 11)` gave us a list of numbers from 1 to 10, and the loop did one iteration for each number in the list. Each time through the loop, the variable `looper` took the next value in the list.

By the way, we called our loop variable `looper`, but you can call it anything you want.

### A matter of style—loop variable names
A loop variable is no different from any other variable. There’s nothing special about it—it’s just a name for a value. It doesn’t matter that we’re using the variable as a loop counter. 

We said before that you should use variable names that describe what the variables do. That’s why I picked the name `looper` for the previous example. But loop variables are one place where you can sometimes make an exception. That’s because there’s a convention (remember, that means a common practice) in programming to use the letters `i`, `j`, `k`, and so on, for loop variables. 

>Why i, j, and k for loops?   
That’s because the early programmers were using programs to ﬁgure out math stuff, and math already uses a, b, c, and x, y, z for other things. Also, in one popular programming language, the variables i, j, and k were always integers—you couldn’t make them any other type. Since loop counters are always integers, they usually picked i, j, and k for their loop counters, and it became common practice.

Because lots of people use `i`, `j`, and k for loop variables, programmers get used to seeing this in programs. It’s perfectly fine to use other names for loop variables, like we did. But you shouldn’t use `i`, `j`, and `k` for anything other than loop variables.

If we used this convention, our program would look like this:
```python
for i in range (1, 5):
    print(i, "times 8 =", i * 8)
```
And it would work exactly the same. (Try it and see!)

Which names you use for your loop variables is a matter of style. Style is about how your programs look, not about whether they work or not. But if you use the same style as other programmers, your programs will be easier to read, understand, and debug. You’ll also be more used to this style, and it’ll be easier for you to read other people’s programs.

### A `range()` shortcut
You don’t always have to give `range()` two numbers like we did in above. You can give it just one number:
```python
for i in range (1, 5):
    print(i, "times 8 =", i * 8)
```
This is the same as writing 
```python
for i in range (0, 5):
```
which gives you this list of numbers: `[0, 1, 2, 3, 4]`.

In fact, most programmers start their loops at 0 instead of 1. If you use `range(5)`, you’ll get 5 iterations of the loop, which is easy to remember. You just have to know that the first time through, `i` will be equal to 0, not 1, and the last time through, it’ll equal 4, not 5.

>So why do most programmers start loops from 0 instead of 1?   
>Well, back in the good old days, some people started from 1 and some people started from 0. They had these really geeky arguments about which one was better. In the end, the 0 people won.   
>So there you have it. Most people start at 0 today, but you can use whichever you like. Just remember to adjust the upper limit so you get the right number 
of iterations.

Just for fun, I tried doing a loop with a string like this:
```python
>>> for letter in "Hi there":
print(letter)
```

A string is like a list of characters. We learned that counting loops use lists for their iterations. That means you can loop through a string. Each character in the string is one iteration through the loop. So if we print the loop variable, which Carter called letter in his example, we’re printing the letters in the string, one at a time. Because each print statement starts a new line, each of the letters prints on its own line.

### Counting by steps
So far, our counting loops have been counting up by 1 each iteration. What if we want the loop to count in steps of 2? Or 5, or 10? What about counting backwards? 

The `range()` function can have an extra argument that allows you to change the size of the steps from the default of 1 to a different size. 

>Arguments are the values that you put inside the parentheses when you use a function like range(). We say that you pass the argument to the function. The term parameter is also used, as in, “pass the parameter”. We’ll learn more about functions, arguments, and parameters soon.

We’re going to try some loops in interactive mode. When you type in the first line, with the colon at the end, IDLE will automatically indent the next line for you, because it knows that a `for` loop needs a block of code following it. When you complete the block of code, press the Enter (or Return) key twice. Try it:
```python
>>> for i in range(1, 10, 2):
    print(i)
1
3
5
7
9
```
We added a third parameter, `2`, to the `range()` function. Now the loop is counting in steps of 2. Let’s try another one:
```python
>>> for i in range (5, 26, 5):
    print(i)
    
5
10
15
20
25
```
Now we’re stepping by 5. How about counting backwards?
```python
>>> for i in range(10, 1, -1):
    print(i)
    
10
9
8
7
6
5
4
3
2
```
When the third parameter in the `range()` function is negative, the loop counts down instead of up. Remember that the loop starts at the first number and goes up to (or down to) but not including the second number, so in our last example we only got down to 2, not 1.

We can use this to make a countdown timer program. We only need to add a couple more lines. try running it. 
```python
import time
for i in range (10, 0, -1):
    print(i)
    time.sleep(1)  
print("BLAST OFF!")
```
Don’t worry about the stuff in the program that I haven’t told you about yet, like `import`, `time`, and `sleep`. We’re going to find out all about that in the following chapters. Just try it and see how it works. The important thing here’s the `range(10, 0, -1)` part, which makes a loop that counts backwards from 10 to 1.

### Counting without numbers
In all the previous examples, the loop variable has been a number. In programming terms, we say that the loop iterates over a list of numbers. But the list doesn’t have to be a list of numbers. As we already saw from Carter’s experiment, it can also be a list of characters (a string). It can also be a list of strings, or anything else. 

The best way to see how this works is with an example.
```python
for cool_guy in ["Spongebob", "Spiderman", "Justin Timberlake", "My Dad"]:
    print(cool_guy, "is the coolest guy ever!")
```
Now we’re not looping over a list of numbers, we’re looping over a list of strings. And instead of `i` for the loop variable, I used `cool_guy`. The loop variable `cool_guy` takes a different value in the list each time through. This is still a kind of counting loop, because even though the list isn’t a list of numbers, Python counts how many items are in the list to know how many times to loop. (I won’t show what the output looks like this time—you’ll see it when you run the program.)

But what if we don’t know ahead of time how many iterations we’ll need? What if there’s no list of values we can use? Don’t touch that dial, because that’s coming up next!

### While we’re on the subject . . .
We just learned about the first kind of loop, a for loop or counting loop. The second kind of loop is called a while loop or conditional loop.

The for loop is great if you know ahead of time how many times you want the loop to run. But sometimes you want a loop to run until something happens, and you don’t know how many iterations it’ll be until that thing happens. While loops let you do that.

In the last chapter, we learned about conditions and testing and the if statement. Instead of counting how many times to run a loop, while loops use a test to decide when to stop a loop. While loops are also called conditional loops. A conditional loop keeps looping while some condition is met.

Basically, a while loop keeps asking “Am I done yet? . . . Am I done yet? . . . Am I done yet? . . .” until it’s done. It’s done when the condition is no longer true.

While loops use the Python keyword `while`. Following shows an example. Type the program in, try it, and see how it works.
```python
print"Type 3 to continue, anything else to quit."
someInput = raw_input()
while someInput == '3': 
    print("Thank you for the 3.  Very kind of you.")
    print("Type 3 to continue, anything else to quit.")  
    someInput = raw_input()
print("That's not 3, so I'm quitting now.")
```
This program keeps asking for input from the user. While the input is equal to 3, the condi-tion is `true`, and the loop keeps running. That’s why this kind of conditional loop is also called a while loop, and it uses the Python `while` keyword. When the input is not equal to 3, the condition is `false`, and the loop stops.

### Bailing out of a loop—break and continue
There are times when you want to get out of a loop in the middle, before a `for` loop is finished counting, or before a `while` loop has found its end condition. There are two ways to do this: you can jump ahead to the next iteration of the loop with `continue`, or you can stop looping altogether with `break`. Let’s look at these more closely.

#### Jumping ahead—`continue`
If you want to stop executing the current iteration of the loop and skip ahead to the next iteration, the continue statement is what you need. The best way to show this is with an example.
```python
for i in range (1, 6):
    print()
    print('i =', i,)
    print('Hello, how',)
    if i == 3:
        continue
    print('are you today?')
```
If we run this program, the output looks like this:
```python
>>> ================== RESTART ==================
>>> 
i = 1 Hello how are you today?
i = 2 Hello how are you today?
i = 3 Hello how
i = 4 Hello how are you today?
i = 5 Hello how are you today?
```
Notice that, the third time through the loop (when `i == 3`), the body of the loop didn’t finish—it jumped ahead to the next iteration (`i == 4`). That was the `continue` statement at work. It works the same way in `while` loops.

#### Bailing out—`break`
What if we want to jump out of the loop completely—never finish counting, or give up waiting for the end condition? The `break` statement does that.

Let’s change only line 6 of listing 8.9, replacing continue with break, and rerun the program to see what happens.
```python
>>> ================== RESTART ==================
>>> 
i = 1 Hello how are you today?
i = 2 Hello how are you today?
i = 3 Hello how
```
This time, the loop didn’t just skip the rest of iteration 3; it stopped altogether. That’s what `break` does. It works the same way in `while` loops. 

I should tell you that some people think using `break` and `continue` is a bad idea. Personally, I don’t think they’re bad, but I rarely use them. I thought I’d tell you about `break` and `continue` just in case you ever need them. 

---

## What did you learn?
In this chapter, you learned about  
&emsp;&emsp;■ `for` loops (also called counting loops).  
&emsp;&emsp;■ the `range()` function—a shortcut for counting loops.  
&emsp;&emsp;■ different step sizes for `range()`.  
&emsp;&emsp;■ `while` loops (also called conditional loops).  
&emsp;&emsp;■ skipping to the next iteration with `continue`.  
&emsp;&emsp;■ jumping out of a loop with `break`.

## Test your knowledge
1. How many times would the following loop run?  
```python
for i in range (1, 6):
    print('Hi, Warren')
```
2. How many times would the following loop run? And what would the values of i be for each loop?  
```python
for i in range (1, 6, 2):
    print('Hi, Warren')
```
3. What list of numbers would `range(1, 8)` give you?  
4. What list of numbers would `range(8)` give you?  
5. What list of numbers would `range(2, 9, 2)` give you?  
6. What list of numbers would `range(10, 0, -2)` give you?  
7. What keyword do you use to stop the current iteration of a loop and jump ahead to the next iteration?  
8. When does a `while` loop end?

## Try it out
1. Write a program to print a multiplication table (a times table). At the start, it should ask the user which table to print. The output should look something like this:  

>Which multiplication table would you like?  
5  
Here's your table:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
5 x 4 = 20  
5 x 5 = 25  
5 x 6 = 30  
5 x 7 = 35  
5 x 8 = 40  
5 x 9 = 45  
5 x 10 = 50

2. You probably used a `for` loop in your program for question #1. That’s how most people would do it. But just for practice, try doing the same thing with a `while` loop. Or if you used a `while` loop in question #1, try it with a `for` loop.  
3. Add something else to the multiplication table program. After asking which table the user wants, ask her how high the table should go. The output should look like this:

>Which multiplication table would you like?  
7  
How high do you want to go?  
12  
Here's your table:  
7 x 1 = 7  
7 x 2 = 14  
7 x 3 = 21  
7 x 4 = 28  
7 x 5 = 35  
7 x 6 = 42  
7 x 7 = 49  
7 x 8 = 56  
7 x 9 = 63  
7 x 10 = 70  
7 x 11 = 77  
7 x 12 = 84  

You can do this with the `for` loop version of the program, the `while` loop version, or both.
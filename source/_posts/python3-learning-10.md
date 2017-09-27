---
title: python3 learning 10
date: 2017-09-22 19:04:51
tags: python3
---
## Collecting Things Together—Lists
We’ve seen that Python can store things in its memory and retrieve them, using names. So far, we have stored strings and numbers (both integers and floats). Sometimes it’s useful to store a bunch of things together in a kind of “group” or “collection.” Then you can do things to the whole collection at once and keep track of groups of things more easily. One of the kinds of collections is a list. In this chapter, we’re going to learn about lists—what they are and how to create, modify, and use them. 
<!-- more -->

Lists are very useful, and they’re used in many, many programs. We’ll use a lot of them in the examples in upcoming chapters when we start doing graphics and game programming, because the many graphical objects in a game are often stored in a list.

### What’s a list?
In Python, you’d write this:
```python
family = ['Mom', 'Dad', 'Junior', 'Baby']
```
or:
```python
luckyNumbers = [2, 7, 14, 26, 30]
```
Both `family` and `luckyNumbers` are examples of Python lists, and the individual things inside lists are called items. As you can see, lists in Python aren’t much different from lists you make in everyday life. Lists use square brackets to show where the list starts and ends, and they use commas to separate the items inside. 

### Creating a list
Both `family` and `luckyNumbers` are variables. We said before that you can assign different kinds of values to variables. We have already used them for numbers and strings, and they can also be assigned a list. 

You create a list like you create any other variable—by assigning something to it, just like we did with `luckyNumbers`. You can also create an empty list, like this:
```python
newList = []
```
There are no items inside the square brackets, so the list is empty. But what good is an empty list? Why would we want to create one?

Well, quite often, we don’t know ahead of time what’s going to be in the list. We don’t know how many items will be in it, or what those items will be. We just know we’ll be using a list to hold them. Once we have an empty list, the program can add things to it. So how do we do that?

### Adding things to a list
To add things to a list, you use `append()`. Try this in interactive mode:
```python
>>> friends = []             #Makes a new, empty list
>>> friends.append('David')  #Adds an item, "David", to the list
>>> print(friends)
```
You’ll get this result:
```python
['David']
```
Try adding another item:
```python
>>> friends.append('Mary')
>>> print(friends)
['David', 'Mary']
```
Remember that you have to create the list (empty or not) before you start adding things to it. It’s like if you are making a cake: you can’t just start pouring ingredients together—you have to get a bowl out first to pour them into. Otherwise you’ll end up with stuff all over the counter! 

### What’s the dot?
Why did we use a dot between `friends` and `append()`? Well, that starts getting into a pretty big topic: objects. 

Many things in Python are objects. To do something with an object, you need the object’s name (the variable name), then a dot, and then whatever you want to do to the object. So to append something to the `friends` list, you’d write this:
```python
friends.append(something)
```

### Lists can hold anything
Lists can hold any kind of data that Python can store. That includes numbers, strings, objects, and even other lists. The items in a list don’t have to be the same type or kind of thing. That means a single list can hold both numbers and strings, for example. A list could look like this:
```python
my_list = [5, 10, 23.76, 'Hello', myTeacher, 7, another_list]
```
Let’s make a new list with something simple, like the letters of the alphabet, so it’s easier to see what’s going on as we learn about lists. Type this in interactive mode:
```python
>>> letters = ['a', 'b', 'c', 'd', 'e']
```

### Getting items from a list
You can get single items from a list by their index number. The list index starts from 0, so the first item in our list is `letters[0]`.
```python
>>> print(letters[0])
a
```
Let’s try another one:
```python
>>> print(letters[3])
d
```

#### Why does the index start from 0, not 1?
That’s a question that a lot of programmers, engineers, and computer scientists have argued about since computers were invented. I’m not going to get in the middle of that argument, so let’s just say the answer is “because,” and move on . . .

Okay, okay! Have a look at “WHAT’S GOING ON IN THERE” to see an explanation of why the index starts at 0 instead of 1.

>Remember that computers use binary digits or bits to store everything. Back in the old days, those bits were expensive. Each one had to be hand-picked and carried by donkey from the bit plantation…just kidding.But they were expensive.

>Binary counting starts at 0. So, to make the most efficient use of the bits and not waste any, things like memory locations and list indices started at 0 as well.

You’ll quickly get used to indices starting at 0. It’s very common in programming. 

### “Slicing” a list
You can also use indices to get more than one item from a list at a time. This is called slicing a list.
```python
>>> print letters[1:4]
['b', 'c', 'd']
```
Similar to the `range()` in our `for` loops, slicing gets the items starting with the first index, but stops before getting to the second index. That’s why we got back three items, not four, in the previous example. One way to remember this is that the number of items you get back is always the difference between the two index numbers. (4 – 1 = 3, and we got three items back.)

Here’s one other thing that is important to remember about slicing a list: What you get back when you slice a list is another (usually smaller) list. This smaller list is called a slice of the original list. The original list isn’t changed. The slice is a partial copy of the original.

Look at the difference here:
```python
>>> print(letters[1])
b
>>> print(letters[1:2])
['b']
```
In the first case, we got back an item. In the second case, we got back a list containing the item. It’s a subtle difference, but you need to know about it. In the first case, we used a sin-gle index to get one item out of the list. In the second case, we used slice notation to get a one-item slice of the list.

To really see the difference, try this:
```python
>>> print(type(letters[1]))
<type 'str'>
>>> print(type(letters[1:2]))
<type 'list'>
```
Displaying the `type` of each one tells you for certain that in one case you get a single item (a string, in this case), and in the other case you get a list.

The smaller list you get back when you slice a list is a copy of items from the original list. That means you can change it and the original list won’t be affected.

#### Slice shorthand
There are some shortcuts you can take when using slices. They don’t really save you much typing, but programmers are a lazy bunch, so they use shortcuts a lot. I want you to know what the shortcuts are, so you can recognize them when you see them in other people’s code and understand what’s going on. That’s important, because looking at other people’s code and trying to understand it is a good way to learn a new programming language, or programming in general.

If the slice you want includes the start of the list, the shortcut is to use a colon followed by the number of items you want, like this: 
```python
>>> print(letters[:2])
['a', 'b']
```
Notice that there is no number before the colon. This will give you everything from the start of the list up to (but not including) the index you specify. 

You can do something similar to get the end of a list:
```python
>>> letters[2:]
['c', 'd', 'e']
```
Using a number followed by a colon gives you everything from the index you specify to the end of the list.

If you don’t put any numbers in, and just use a colon, you get the whole list:
```python
>>> letters[:]
['a', 'b', 'c', 'd', 'e']
```
Remember that I said that slices make a copy of the original? So `letters[:]` makes a copy of the whole list. This is handy if you want to make some changes to a list but keep the original unchanged.

### Modifying items
You can use the index to change one of the list items:
```python
>>> print(letters)
['a', 'b', 'c', 'd', 'e']
>>> letters[2] = 'z'
>>> print(letters)
['a', 'b', 'z', 'd', 'e']
```
But you can’t use the index to add new items to the list. Right now, there are five items in the list, with indices from 0 to 4. So we could not do something like this:

It would not work. (Try it if you want.) It’s like trying to change something that isn’t there yet. To add items to a list, you have to do something else, and that’s where we’re going next. But before we do, let’s change our list back to the way it was:
```python
>>> letters[2] = 'c'
>>> print(letters)
['a', 'b', 'c', 'd', 'e']
```

### Other ways of adding to a list
We already saw how to add things to a list using `append()`. But there are other ways. In fact, there are three methods for adding things to a list: `append()`, `extend()`, and `insert()`.  
&emsp;&emsp;■ `append()` adds one item to the end of the list.  
&emsp;&emsp;■ `extend()` adds multiple items to the end of the list.  
&emsp;&emsp;■ `insert()` adds one item somewhere in the list, not necessarily at the end. You tell it where to add the item.

#### Adding to the end: `append()`
We already saw how `append()` works. It adds one item to the end of a list:
```python
>>> letters.append('n')
>>> print(letters)
['a', 'b', 'c', 'd', 'e', 'n']
```
Let’s add one more:
```python
>>> letters.append('g')
>>> print(letters)
['a', 'b', 'c', 'd', 'e', 'n', 'g']
```
Notice that the letters are not in order. That’s because append() adds the item to the end of the list. If we want the items in order, we’ll have to sort them. We’ll get to sorting very soon.

#### Extending the list: `extend()`
`extend()` adds several items to the end of a list:
```python
>>> letters.extend(['p', 'q', 'r'])
>>> print(letters)
['a', 'b', 'c', 'd', 'e', 'n', 'g', 'p', 'q', 'r']
```
Notice that what’s inside the round brackets of the `extend()` method is a list. A list has square brackets, so for `extend()`, you could have both round and square brackets.

Everything in the list you give to `extend()` gets added to the end of the original list.

#### Inserting an item: `insert()`
`insert()` adds a single item somewhere in the list. You tell it at what position in the list you want the item added:
```python
>>> letters.insert(2, 'z')
>>> print(letters)
['a', 'b', 'z', 'c', 'd', 'e', 'n', 'g', 'p', 'q', 'r']
```
Here, we added the letter z at index 2. Index 2 is the third position in the list (because the indices start at 0). The letter that used to be in the third position, c, got bumped over by one place, to the fourth position. Every other item in the list also got bumped one position.

#### The difference between `append()` and `extend()`
Sometimes `append()` and `extend()` look very similar, but they do different things. Let’s go back to our original list. First, try using `extend()` to add three items:
```python
>>> letters = ['a','b','c','d','e']
>>> letters.extend(['f', 'g', 'h'])
>>> print(letters)
['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']
```
Now, we’ll try to use `append()` to do the same thing:
```python
>>> letters = ['a', 'b', 'c', 'd', 'e']
>>> letters.append(['f', 'g', 'h'])
>>> print(letters)
['a', 'b', 'c', 'd', 'e', ['f', 'g', 'h']]
```
What happened here? Well, we said before that `append()` adds one item to a list. How did it add three? It didn’t. It added one item, which happens to be another list containing three items. That’s why we got the extra set of square brackets inside our list. Remember that a list can hold anything, including other lists. That’s what we’ve got.

`insert()` works the same way as `append()`, except that you tell it where to put the new item. `append()` always puts it at the end.

### Deleting from a list
How do we delete or remove things from a list? There are three ways: remove(), del, and `pop()`.

#### Deleting with `remove()`
`remove()` deletes the item you choose from the list and throws it away:
```python
>>> letters = ['a', 'b', 'c', 'd', 'e']
>>> letters.remove('c')
>>> print(letters)
['a', 'b', 'd', 'e']
```
You don’t need to know where in the list the item is. You just need to know it’s there somewhere. If you try to remove something that isn’t in the list, you’ll get an error:
```python
>>> letters.remove('f')
Traceback (most recent call last):
  File "<pyshell#32>", line 1, in -toplevel-
    letters.remove('f')
ValueError: list.remove(x): x not in list
```
So how can you find out if a list contains a certain item? That’s coming right up. First, let’s look at the other ways to delete something from a list.

#### Deleting with `del`
`del` lets you delete an item from the list using its index, like this:
```python
>>> letters = ['a', 'b', 'c', 'd', 'e']
>>> del letters[3]
>>> print(letters)
['a', 'b', 'c', 'e']
```
Here, we deleted the fourth item (index 3), which was the letter d.  

#### Deleting with pop()
`pop()` takes the last item off the list and gives it back to you. That means you can assign it a name, like this:
```python
>>> letters = ['a', 'b', 'c', 'd', 'e']
>>> lastLetter = letters.pop()
>>> print(letters)
['a', 'b', 'c', 'd']
>>> print(lastLetter)
e
```
You can also use `pop()` with an index, like this:
```python
>>> letters = ['a', 'b', 'c', 'd', 'e']
>>> second = letters.pop(1)
>>> print(second)
b
>>> print(letters)
['a', 'c', 'd', 'e']
e
```
Here, we popped the second letter (index 1), which was b. The item we popped was assigned to `second`, and it was also removed from `letters`.

With nothing inside the parentheses, `pop()` gives you the last item and removes it from the list. If you put a number in the parentheses, `pop(n)` gives you the item at that index and removes it from the list.

### Searching a list
Once we have several items in a list, how do we find them? Two things you’ll often need to do with a list are  
&emsp;&emsp;■ find out whether an item is in a list or not.  
&emsp;&emsp;■ find out where an item is in the list (its index).

#### The `in` keyword
To find out whether something is in a list, you use the `in` keyword, like this:
```python
if 'a' in letters:
    print("found 'a' in letters")
else:
    print("didn't find 'a' in letters")
```
The `'a' in letters` part is a Boolean or logical expression. It’ll return the value `True` if a is in the list, and `False` otherwise.

You can try this in interactive mode:
```python
>>> 'a' in letters
True
>>> 's' in letters
False
```
This is telling us that the list called `letters` does have an item a, but it does not have an item s. So a is in the list, and s isn’t in the list. Now you can combine `in` and `remove()`, and write something that won’t give you 
an error, even if the value isn’t in the list:
```python
if 'a' in letters:
    letters.remove('a')
```
This code only removes the value from the list if the value is in the list.

#### Finding the index
To find where in the list an item is located, you use the `index()` method, like this:
```python
>>> letters = ['a', 'b', 'c', 'd', 'e']
>>> print(letters.index('d'))
3
```
So we know that d has index 3, which means it’s the fourth item in the list.

Just like `remove()`, `index()` will give you an error if the value isn’t found in the list, so it’s a good idea to use it with in, like this:
```python
if 'd' in letters:
    print(letters.index('d'))
```

### Looping through a list
When we first talked about loops, we saw that loops iterate through a list of values. We also learned about the `range()` function and used it as a shortcut for generating lists of num-bers for our loops. You saw that `range()` gives you a list of numbers.

But a loop can iterate through any list—it doesn’t have to be a list of numbers. Let’s say we wanted to print our list of letters with one item on each line. We could do something like this:
```python
>>> letters = ['a', 'b', 'c', 'd', 'e']
>>> for letter in letters:
    print(letter)
    
a
b
c
d
e
>>> 
```
This time, our loop variable is `letter`. (Before, we used loop variables like `looper` or `i`, `j`, and `k`.) The loop iterates over (loops through) all the values in the list, and each time through, the current item is stored in the loop variable, `letter`, and then is displayed.

### Sorting lists
Lists are an ordered type of collection. This means the items in a list have a certain order, and each one has a place, its index. Once you have put items in a list in a certain order, they stay in that order unless you change the list with insert(), append(), remove(), or pop(). But that order might not be the order you want. You might want a list sorted before you use it. 

To sort a list, you use the sort() method. 
```python
>>> letters = ['d', 'a', 'e', 'c', 'b']
>>> print(letters)
['d', 'a', 'e', 'c', 'b']
>>> letters.sort()
>>> print(letters)
>>> ['a', 'b', 'c', 'd', 'e']
```
`sort()` automatically sorts strings alphabetically and numbers numerically, from smallest to largest.

It’s important to know that `sort()` modifies the list in place. That means it changes the original list you give it. It does not create a new, sorted list. That means you can’t do this:
```python
>>> print(letters.sort())
```
If you do, you’ll get “None.” You have to do it in two steps, like this:
```python
>>> letters.sort()
>>> print(letters)
```

#### Sorting in reverse order
There are two ways to get a list sorted in reverse order. One is to sort the list the normal way, and then reverse the sorted list, like this:
```python
>>> letters = ['d', 'a', 'e', 'c', 'b']
>>> letters.sort()
>>> print(letters)
['a', 'b', 'c', 'd', 'e']
>>> letters.reverse()
>>> print(letters)
['e', 'd', 'c', 'b', 'a']
```
Here we saw a new list method called `reverse()`, which reverses the order of items in a list.

The other way is to add a parameter to `sort()` to make it sort in descending order (from largest to smallest). 
```python
>>> letters = ['d', 'a', 'e', 'c', 'b']
>>> letters.sort (reverse = True)
>>> print(letters)
['e', 'd', 'c', 'b', 'a']
```
The parameter is called `reverse`, and it does exactly what you’d expect—it makes the list sort in reverse order.

Remember that all of the sorting and reversing we just talked about modifies the original list. That means your original order is lost. If you want to preserve the original order and sort a copy of the list, you could use slice notation, which we talked about earlier in this chapter, to make a copy—another list equal to the original:
```python
>>> original_list = ['Tom', 'James', 'Sarah', 'Fred']
>>> new_list = original_list[:]
>>> new_list.sort()
>>> print(original_list)
['Tom', 'James', 'Sarah', 'Fred']
>>> print(new_list)
['Fred', 'James', 'Sarah', 'Tom']
```
We sorted `new`, but `original` also got sorted, because `new` and `original` are just two different names for the same list. There are not two different lists.

This means that, if you really want to make a copy of a list, you need to do something different from `new = original`. The easiest way to do this is to use slice notation, like I did above: `new = original[:]`. This means “copy everything in the list, from the first item to the last item.” 

There are now two separate lists. We made a copy of the original and called it `new`. Now if we sort one list, the other one won’t be sorted.

#### Another way to sort—`sorted()`
There is another way to get a sorted copy of a list without changing the order of the original list. Python has a function called `sorted()` for that purpose. It works like this:
```python
>>> original = [5, 2, 3, 1, 4]
>>> newer = sorted(original)
>>> print(original)
[5, 2, 3, 1, 4]
>>> print(newer)
[1, 2, 3, 4, 5]
```
The `sorted()` function gives you a sorted copy of the original list.

### Mutable and immutable
If you remember back to chapter 2, we said that you couldn’t actually change a number or string, you could only change what number or string a name was assigned to (in other words, move the tag). But lists are one of the types in Python that can be changed. As we just saw, lists can have items appended or deleted, and the items can be sorted or reversed.

These two different kinds of variables are called mutable and immutable. Mutable just means “able to be changed” or “changeable.” Immutable means “not able to be changed” or “unchangeable.” In Python, numbers and strings are immutable (cannot be changed), and lists are mutable (can be changed).

#### Tuple—an immutable list
There are times when you don’t want a list to be changeable. So, is there an immutable kind of list in Python? The answer is yes. There is a type called a tuple, which is exactly that, an immutable (unchangeable)list. You make one like this:
```python
my_tuple = ("red", "green", "blue")
```
You use round brackets, instead of the square ones that lists use. 

Because tuples are immutable (unchangeable), you can’t do things like sort them or append or delete items. Once you create a tuple with a set of items, it stays that way.

### Lists of lists: tables of data
When thinking about how data is stored in a program, it’s useful to visualize it.

A variable has a single value. [myTeacher >>> Mr. Wilson]

A list is like a row of values strung together. [myFriends >>> Kim Curtis Shaun Jenn Karla]

Sometimes you need a table with rows and columns.

How can we save a table of data? We already know that we can make a list to hold several items. We could put each student’s marks in a list, like this:
```python
>>> joeMarks = [55, 63, 77, 81]
>>> tomMarks = [65, 61, 67, 72]
>>> bethMarks = [97, 95, 92, 88]
```
or we could use a list for each subject, like this:
```python
>>> mathMarks = [55, 65, 97]
>>> scienceMarks = [63, 61, 95]
>>> readingMarks = [77, 67, 92]
>>> spellingMarks = [81, 72, 88]
```
But we might want to collect all the data together in a single data structure. 

>A data structure is a way of collecting, storing, or representing the data in a program. Data structures can include variables, lists, and some other things we haven’t talked about yet. The term data structure really refers to the way the data is organized in a program. 

To make a single data structure for our class marks, we could do something like this:
```python
>>> classMarks = [joeMarks, tomMarks, bethMarks]
>>> print(classMarks)
[[55, 63, 77, 81], [65, 61, 67, 72], [97, 95, 92, 88]]
```
This gives us a list of items, where each item is itself a list. We have created a list of lists. Each of the items in the `classMarks` list is itself a list.

We could also have created `classMarks` directly, without first creating `joeMarks`, `tomMarks`, and `bethMarks`, like this:
```python
>>> classMarks = [ [55,63,77,81], [65,61,67,72], [97,95,92,88] ]
>>> print(classMarks)
[[55, 63, 77, 81], [65, 61, 67, 72], [97, 95, 92, 88]]
```
Now let’s try displaying our data structure. `classMarks` has three items, one for each student. So we can just loop through them using `in`:
```python
>>> for studentMarks in classMarks:
    print(studentMarks)
    
[55, 63, 77, 81]
[65, 61, 67, 72]
[97, 95, 92, 88]
```
Here we looped through the list called classMarks. The loop variable is studentMarks. Each time through the loop, we print one item in the list. That one item is the marks for a single student, which is itself a list. (We created the student lists above.)

Notice that this looks very similar to the table on the previous page. So we have come up with a data structure to hold all our data in one place.

#### Getting a single value from the table
How do we get access to values in this table (our list of lists)? We already know that the first student’s marks (`joeMarks`) are in a list that is the first item in `classMarks`. Let’s check that:
```python
>>> print(classMarks[0])
[55, 63, 77, 81]
```
`classMarks[0]` is a list of Joe’s marks in the four subjects. Now we want a single value from `classMarks[0]`. How do we do that? We use a second index. 

If we want the third of his marks (his Reading mark), which has index 2, we’d 
do this:
```python
>>> print(classMarks[0][2])
77
```
This gave us the first item in `classMarks` (index 0), which was the list of Joe’s marks, and the third item in that list (index 2), which was his Reading mark. When you see a name with two sets of square brackets, like `classMarks[0][2]`, that is usually referring to a list of lists.

The `classMarks` list doesn’t really know about the names Joe, Tom, and Beth, or the subjects Math, Science, Reading, and Spelling. We labeled them that way because we know what we intended to store in the list. But to Python, they’re just numbered places in a list. This is just like the numbered mailboxes at a post office. They don’t have names on them, just numbers. The postmaster keeps track of what belongs where, and you know which box is yours. 

A more accurate way to label the classMarks table would be like this:
![classMarks table](https://github.com/changemyheart/Pictures/blob/master/classMarks%20table.png?raw=true)
Now it’s easier to see that the mark 77 is stored in `classMarks[0][2]`.

If we were writing a program using `classMarks` to store our data, we’d have to keep track of which data was stored in which row and column. Just like the postmaster, we’d have the job of keeping track of which slot belongs to which piece of data.

---

## What did you learn?
In this chapter, you learned   
&emsp;&emsp;■ what lists are.  
&emsp;&emsp;■ how to add things to a list.  
&emsp;&emsp;■ how to delete things from a list.  
&emsp;&emsp;■ how to find out if a list contains a certain value.  
&emsp;&emsp;■ how to sort a list.  
&emsp;&emsp;■ how to make a copy of a list.  
&emsp;&emsp;■ about tuples.  
&emsp;&emsp;■ about lists of lists.

## Test your knowledge
1. What are two ways to add something to a list?
2. What are two ways to remove something from a list?
3. What are two ways to get a sorted copy of a list, without changing the original list?
4. How do you find out whether a certain value is in a list?
5. How do you find out the location of a certain value in a list?
6. What’s a tuple?
7. How do you make a list of lists?
8. How do you get a single value from a list of lists?

## Try it out
1. Write a program to ask the user for five names. The program should store the 
names in a list, and print them all out at the end. It should look something like this:
```python
Enter 5 names:
Tony
Paul
Nick
Michel
Kevin
The names are Tony Paul Nick Michel Kevin 
```
2. Modify the program from question #1 to print both the original list of names and a sorted list.
3. Modify the program from question #1 to display only the third name the user typed in, like this:
```python
The third name you entered is:  Nick
```
4. Modify the program from question #1 to let the user replace one of the names. She should be able to choose which name to replace, and then type in the new name. Finally, display the new list like this:
```python
Enter 5 names:
Tony
Paul
Nick
Michel
Kevin
The names are Tony Paul Nick Michel Kevin
Replace one name.  Which one? (1-5): 4
New name: Peter
The names are Tony Paul Nick Peter Kevin
```

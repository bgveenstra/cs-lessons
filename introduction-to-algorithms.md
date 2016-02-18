---
title: Introduction to Algorithms
type: lesson
duration: "1:15"
creator:
    name:
    city: SF
competencies: Programming, Computer Science
---

# Introduction to Algorithms 

### Objectives
*After this lesson, students will be able to:*

- Define "algorithm" and explain how algorithms can speed up software development.   
- Distinguish between iterative and recursive algorithms and trace recursive function calls.   
- Analyze the time and memory requirements of common patterns like for loops.  

### Preparation
*Before this lesson, students should already be able to:*

- Trace the flow of a program based on its code, including conditionals, loops, and function calls.   
- Interpret notation for exponents (a<sup>2</sup>) and logarithms (log<sub>2</sub>c).


##Algorithm Efficiency and Big-O Notation


Discuss the following in small groups:

* Why is it useful to follow established design patterns? 

* How has the work of other developers helped you in the past?

##What is an algorithm?

A set of instructions to find the solution to a problem.

Note: we use code to *implement* algoritms, but algorithms don't have to be expressed in code. It's usually better to talk through or write out the general strategy of an algorithm before trying to code it.

##What is efficiency?

Time efficiency helps us predict how long it could take a particular algorithm to run. Space efficiency helps us predict how much memory a particular algorithm could use up.

##Why study algorithms and efficiency?

* Understanding algorithms let us reuse knowledge from the field.

* Better-performing algorithms can enhance the user experience by decreasing wait times or improving results.

* Better-performing algorithms can save companies money by reducing equipment needs.

* Algorithms and algorithm analysis are an important part of the shared language developers use to talk about programs (especially in **INTERVIEWS!**).


##Big O notation

Big O notation gives us a simplified way to talk about the  time and space requirements of an algorithm (often called time and space "complexity").  

1. Ask yourself: In the worst case scenario, about how many calculations does your algorithm do?
2. Phrase the answer in terms of the size of the input.  
3. Ignore constant multiples or smaller things added on.



If we tried to get a 100% accurate picture of how long an algorithm would take, the analysis would be so complex it wouldn't be useful at all.  So Big O notation makes step one above WAY easier by pretending computers are simpler than they actually are. Big O uses the RAM model of computation and assumes all computers ares simple "Random-Access Machines."  (Don't confuse this with Random Access Memory, the RAM memory inside actual computers.) This simplified model means that instead of answers like "This algorithm will do exactly 37 operations for each bit of data in the input, plus 45 to calculate an if statement, plus..." we get answers like "This algorithm is O(n)".  Big O notation usually looks like this:  O(1), O(log(n)), O(n), O(n*log(n)), O(n<sup>2</sup>), O(2<sup>n</sup>)...  where `n` is the size or number of inputs.  It's important to remember that Big O notation gives an upper limit for how long or how much space an algorithm could take.  It's like a "less than or equal to":  

An algorithm is O(n) if (and only if) the time it takes to complete the algorithm is **less than or equal to** some constant multiple of the number of inputs.  

### Big O Guidelines

#### O(1) operations

To say an algorithm takes O(1) time means no matter how big the input(s) are, the computer will do basically same amount of work to perform the algorithm on them.

We will consider all mathematical operations on normal-size numbers or characters O(1).  In Big O notation, these are **O(1)** operations: `+`, `-`, `*`, `/`, and `%`.  

```js
function add(a,b){
    return a+b;
}
```

We also assume that comparisons ( `<` ) are constant time operations, and that handling for `if`s and `returns` is pretty much constant time too.

#### O(n)

To say an algorithm takes O(n) time means that the computer will do more work to perform the algorithm if the inputs are larger or if there are more inputs -- *and* that the increase in work done mirrors the incresase in the size or number of inputs.

Functions containing loops that go through the whole input are generally implementing at least **O(n)** algorithms.

```js
function addAll(numArray){
    var sum = 1;
    for (var i=0; i<numArray.length; i++){
        sum +=  numArray[i];
    }
    return sum;
}
```

####O(log(n)) or O(n*log(n))

Logarithm terms in Big O notation usually come from recursive functions that divide the problem into smaller subproblems.



####Combinations

Almost everything else is composed of combinations of those. For example, if a for loop has more complex operations inside it, time complexity is usually higher.

```js
function addAllArrays(arrayOfArrays){
    var sum = 1;
    var oneArray;
    for (var i=0; i<arrayOfArrays.length; i++){
        oneArray = arrayOfArrays[i];
        for (var j=0; j<oneArray.length; j++){
            sum +=  numArray[j];
        }
    }
    return sum;
}
```


Graph: how the number of operations (time) grows with the number of input    
elements for various orders of complexity   
![time complexity graph from daveperrett.com](http://www.daveperrett.com/images/articles/2010-12-07-comp-sci-101-big-o-notation/Time_Complexity.png)

#####Related Notations

Big O is the most commonly-used notations for comparing functions in computer science, but there are others:

| notation | analogy |
| :----: | :----: |
| algorithm is o(g(n)) | time < constant * g(n) |
| **algorithm is O(g(n))** | **time <= constant * g(n)** |
| algorithm is Θ(g(n)) | time == constant * g(n) |
| algorithm is Ω(g(n)) | time >= constant * g(n) |
| algorithm is ω(g(n)) | time > constant * g(n) |


#### More Big O Resources

* reading from [Interview Cake](https://www.interviewcake.com/article/big-o-notation-time-and-space-complexity)
* <a href="http://bigocheatsheet.com" target="_blank">Big-O Cheat Sheet</a>
* <a href="https://rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation" target="_blank">A beginner's guide to Big O notation - Rob Bell</a>

## Break!

## Algorithms

That was all pretty abstract! Let's look at an example of one problem and two different approaches to solve it - two different algorithms!

The problem we'll examine is how to search for a number within an array. We'll start with a target value (say 8) and an array, like `[0,4,5]`.  The algorithm should give us the index of the target number in the array, if it's in there, or some other value (let's say `null` or `nil` if it's not there). If the target is in the array multiple times, we'll accept any index where it occurs.

> We do binary search:

> Have each student write a number on a piece of paper, large enough so that it can be seen from far away. They can choose any number. 

> Once each person has chosen a number, have the students stand up in sorted order. 

> Have one student (or a coinstructor) pick any number, not worrying about whether it's on one of the cards or not. If you're picking the number, choose one next to the middle (but not in the middle)!

> Tell the students they are an array, and have them count off their indices.

> Ask for a simple way to search through the array for the target number.  Hopefully you'll get a brute force suggestion.  Starting with index 0 (the student with the lowest number), have the students execute a brute force search for the number.  Especially if the number was early in the array, ask how many students they'd have to check for a number that isn't in the array. They should realize it would require looking at everyone's number in order. 

> Tell them that since they're sorted they can do a little better. Ask for suggestions, and move forward with finding the middle of the array.  Make sure to calculate the middle "index". Ask three quesitons. For example, if the target is 43: Are you 43? Are you greater than 43? Are you less than 43?   "Discard" the students whose numbers are in the wrong half of the array.  Ask how to move forward now, and carry on until you find the target or figure out it's not in the array.  

Here's some code for our simple search algorithm:

```js
function simple_search(target, arr){
    for (var i = 0; i < arr.length; i++){
        if (arr[i] === target){
            return i;
        }
    }
    return null;
}
```

In a small group, discuss: What is the Big O time complexity the simple search algorithm (which this function implements)?

#### Recursion and Binary Search

Binary search is faster.  We saw that it could take many more tries to find the target number (or decide it wasn't in the array) with the simple search algorithm than with binary search. To express how much faster binary search is, we turn to Big O notation. 

Here's some pseudocode for an iterative binary search:

- take in an array, `arr`
- track two values: `low` and `high` - the boundaries of the part of the array the target might be in
- `low` starts at `0`, and `high` starts at `arr.length-1`
- find the middle index of the array, and compare the number there to the target number
    - if the target is the same as the number in the middle of the array, return the middle index
    - if the target is bigger than the number in the middle of the array, set `low` to the middle index (why?)
    - if the target is smaller, set `high` to the middle index
- keep finding and checking the middle until you either find the target or run out of numbers to check

```js
function binary_search(target, arr) {
    var low = 0, high = arr.length-1, mid;
    while (high - low >= 1){
        mid = (high - low)/2;
        if (target === mid) {
            return mid;
        } else if (target > mid) {
            low = mid;
        } else {
            high = mid;
        }
    }
    return null;
}
```


###Recursion 

A "recursive" function (or algorithm) invokes itself as part of its problem solving. (Functions that aren't recursive are "iterative.")  Run this recursive function:

```ruby
def recurse(depth)
  if depth > 0
    puts "Spiraling down..."
    recurse(depth - 1)
    puts "Spiraling up..."
  else
    puts "Bottom of the rabbit hole"
  end
end

recurse 5
```

When you write a recursive function, you always need a base case (where the recursion should stop) and a recursive case (when the recursive function should keep calling itself). 

<details><summary>What is the base case for the recursive function above? How can you tell?</summary>
The base case is when `depth` is less than or equal to `0`. You can tell because the `else` part of the function doesn't call the entire function again, but the `if` part did. </details>

<details><summary>What is the recursive case for the function above?</summary>
The recursive case is when `depth > 0`, because any time that's true the function will get called again.</details>

#### The Call Stack

Most programming languages rely on something called the "call stack," especially for recursion. The call stack keeps track of function calls that are in the process of executing.  When a function is called, it's `push`ed onto the call stack. When the function returns, it's `pop`ed off of the stack.

Here's a recursive `factorial` method:

```ruby
def factorial(num)
   if num > 1
      num * factorial(num-1)
   elsif num == 1 or num == 0
      1
   else
      puts "can't do factorial of a negative number!"
   end
end

factorial(4)
# => 24
```

Here's a diagram that shows how the computer uses the "call stack" to keep track of the recursive function calls it needs to complete to calculate 4 factorial:

![call stack diagram](http://i.stack.imgur.com/PK6Ht.png)



**Working with a partner, draw a call stack diagram for the `recurse 5` method call above.**

**Working with a partner, draw a call stack diagram for a recursive binary search algorithm with target 10 and input array [8, 10, 12, 13, 12, 15].**

###Calculating Big O for Recursive Functions

There are a few ways to calculate Big O for recursive functions.

####Recursion Trees

The call stack is inherently tied to how a processor handles function calls. But algorithms don't always have to be implemented in functions! When we think of recursive algorithms, we can draw them as recursion "trees." 

![recursion tree for fibonacci](https://users.soe.ucsc.edu/~fire/dev-2008f-12/labs/lab8-Recursion-vs-Iteration/fib_5.png)

####Math

Many recursive algorithms can be modeled with this formula:

T(n) = aT(n/b) + O(1)

where T(n) is the time it takes to calculate the answer for input size n, a is the number of subproblems you have to figure out to get the answer, n/b is the size of each subproblem, and the O(1) stands for some small extra amout of work to combine the answers to the subproblems.   

This will be clearer with an example. For the recursive binary search algorithm, the equation would be:

T(n) = 1*T(n/2) + O(1)




###Discuss


<details><summary>Would our simple search algorithm work on an unsorted array?</summary>Yes!</details>

<details><summary>Would binary search work on an unsorted array?</summary>No! We wouldn't be able to reliably eliminate half of the array. </details>

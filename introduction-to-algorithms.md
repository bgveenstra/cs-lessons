---
title: Introduction to Algorithms
type: lesson
duration: "1:15"
creator:
    name:
    city: SF
competencies: Programming, Computer Science
---

# Introduction to Algorithms and Data Structures

### Objectives
*After this lesson, students will be able to:*

- Define "algorithm" and explain how algorithms can speed up software development.   
- Distinguish between iterative and recursive algorithms and trace recursive function calls.   
- Analyze the time and memory requirements of common patterns like for loops.  

### Preparation
*Before this lesson, students should already be able to:*

- Trace the flow of a program based on its code, including conditionals, loops, and function calls.   

- Explain how computers store information and how programs manipulate data stored in memory.   


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

<!--@TODO: more!-->



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


##Resources

* reading from [Interview Cake](https://www.interviewcake.com/article/big-o-notation-time-and-space-complexity)
* <a href="http://bigocheatsheet.com" target="_blank">Big-O Cheat Sheet</a>
* <a href="https://rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation" target="_blank">A beginner's guide to Big O notation - Rob Bell</a>


## Algorithms

 - simple search
 - binary search (& which data structures this works with?!)

 Today we're going to look at two different algorithms for searching for a number within an array. 

 We do binary search:

 Have each student write a number on a piece of paper, large enough so that it can be seen from far away. They can choose any number. 

 Once each person has chosen a number, have the students stand up in sorted order. 

 Have one student (or a coinstructor) pick any number, not worrying about whether it's on one of the cards or not. If you're picking the number, choose one next to the middle (but not in the middle)!

Tell the students they are an array, and ask for one way to search through the array for the target number.  Hopefully you'll get a brute force suggestion.  Starting with index 0 (the student with the lowest number), have the students execute a brute force search for the number.  Especially if the number was early in the array, ask how many students they'd have to check for a number that isn't in the array. They should realize it would require looking at everyone's number in order. 

Tell them that since they're sorted they can do a little better. Ask for suggestions, and move forward with finding the middle of the array.  Ask three quesitons. For example, if the target is 43: Are you 43? Are you greater than 43? Are you less than 43?   "Discard" the students whose numbers are in the wrong half of the array.  Ask how to move forward now, and carry on until you find the target or figure out it's not in the array.  


 - recursion refresher & implement binary search (20 minutes)
 - binary search is indeed faster -> big oh notation

 Binary search seemed faster.  (Examples with counting how many comparisons are made.)  To get a feel for how much faster it is, we use Big Oh notation.  To calculate the Big Oh of binary search, we'll have to look a little more at recursion.  

 Iterative and recursive versions of binary search. 


 Now binary search is faster than simple search, but it requires that the input array be sorted. Let's look at a few different sorting algorithms.

 - simple sort (bubble? insertion?)
 - merge sort 
 - quick sort?


## Conclusion (5 mins)
- Ask some questions
- See if anyone learned what they were supposed to
- See if you did a good job by teaching them stuff

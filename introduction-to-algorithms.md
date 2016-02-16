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


  Why is it useful to follow established design patterns? How has the work of other web developers or programmers helped you in the past?

##What is an algorithm?


A set of instructions to find the solution to a problem.

Note: we use code to implement algoritms, but algorithms don't have to be written in code.

##What is efficiency?

Time efficiency helps us predict how long it could take a particular algorithm to run. Space efficiency helps us predict how much memory a particular algorithm could use up.

##Why study algorithms and efficiency?

* Understanding algorithms let us reuse knowledge from the field.
* Better-performing algorithms can enhance the user experience.
* Better-performing algorithms can save companies money.
* Algorithms and algorithm analysis are shared languages developers use to talk programs (especially in INTERVIEWS!).


##Big O notation

1. Ask yourself: In the worst case scenario, about how many calculations does your algorithm do?
2. Phrase the answer in terms of the size of the input.  
3. Ignore constant multiples or smaller things added on.

We will consider all mathematical operations constant time or **O(1)** operations: `+`, `-`, `*`, `/`, and `%`.

```js
function add(a,b){
    return a+b;
}
```

Functions containing for loops that go through the whole input are generally implementing at least linear time or **O(n)** algorithms.

```js
function addAll(numArray){
    var sum = 1;
    for (var i=0; i<numArray.length; i++){
        sum +=  numArray[i];
    }
    return sum;
}
```

Logarithm terms in Big O notation (like O(log(n)) usually come from recursive functions that divide the problem into smaller subproblems. Well see more about recursive algorithms as we go.

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

###Bonus: Related Notations

Big O is the most commonly-used notations for comparing functions in computer science, but there are others:

| notation | analogy |
| :----: | :----: |
| **f(n) = O(g(n))** | **<=** |
| f(n) = o(g(n)) |  <= |
| f(n) = Θ(g(n)) | = |
| f(n) = Ω(g(n)) | > |
| f(n) =  ω(g(n)) | < |


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

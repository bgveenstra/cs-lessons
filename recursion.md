---
title: Recursion
type: lesson??
duration: "1:20"
creator:
    name:
    city: SF
competencies: Programming, Computer Science

---

# Recursion 

## Introduction (10 minutes)

### Objectives
*After this lesson, students will be able to:*

- Distinguish between iterative and recursive algorithms and trace recursive function calls.  

- Analyze the time and memory requirements of algorithms with Big O notation.

### Preparation
*Before this lesson, students should already be able to:*

- Trace the flow of a program based on its code, including conditionals, loops, and function calls.   

- Interpret notation for exponents (a<sup>2</sup>) and logarithms (log<sub>2</sub>c).

- Define "algorithm" and explain how algorithms can speed up software development.   

- Recognize Big O time requirements of common patterns like for loops.  



####O(log(n)) or O(n*log(n))

Logarithm terms in Big O notation usually come from recursive functions or scenarios where we use the "divide and conquer" approach. For interview prep purposes, some good rules of thumb are:

* searching through a sorted array takes O(log(n)) time  
* sorting an array takes O(n*log(n)) time


s of numbers, find the largest sum of two numbers where one comes from each of the arrays. 


#### Binary Search

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

##Divide and Conquer

Binary search is a great example of the "divide and conquer" approach!  We start with an input array of size n and n possibile locations where the target value could be in the array (or one possibility that it's not in the array).  

Each time we make a comparison in binary search, we're able to eliminate half the array - we cut the problem size in half.  
We saw that it took  log<sub>2</sub>(n) steps to go from a problem size of n+1 to 1, since we're dividing the problem size by 2 at each step.  Since each step did O(1) work, the total time requirement for binary search is O(log(n)).


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

<!--###Calculating Big O for Recursive Functions-->

<!--There are a few ways to calculate Big O for recursive algorithms.  One conceptually simple but powerful tool is a recurrence relation. Each recurrence relation is a math equation, but it's totally within reach even if it's been a while since you touched algebra. First, it gives a name to the time it takes to solve a problem with some input size `x` - this will be `T(x)`. So the time the algorithm needs for our tpical input size `n` is called `T(n)`.  Here's the key part: it uses the specifics of the algorithm to phrase `T(n)` in terms of the time required for recursive calls the function makes (or recursive invocations of the algorithm).  Finally, it takes into account the extra work that has to be done to go from the recursive call answers back to the full answer for `T(n)`; this extra work is usually simplified to Big O notation.-->

<!--Let's look at factorial again. Here's pseudocode:-->

<!--```python-->
<!--def factorial(n):-->
<!--    if n <= 1:-->
<!--        return 1-->
<!--    else:-->
<!--        return n * factorial (n-1)-->
<!--```-->

<!--This translates to the following reccurrence relation:-->

<!--`T(n) = T(n-1) + O(1)`.-->

<!--Here's fibonacci:-->

<!--```python-->
<!--def fib(n):-->
<!--    if n < 0:-->
<!--        return 0-->
<!--    else if n <= 1:-->
<!--        return 1-->
<!--    else:-->
<!--        return fib(n-1) + fib(n-2)-->
<!--```-->

<!--<details>-->
<!--    <summary>Write a recurrence relation for recursive binary search.</summary>-->
<!--    `T(n) = T(n/2) + O(1)`-->
<!--</details>-->

<!--<details>-->
<!--    <summary>Write a recurrence relation for recursive binary search.</summary>-->
<!--    `T(n) = T(n/2) + O(1)`-->
<!--</details>-->


<!--Cheatsheet-->
<!--<table>-->
<!--  <tr>-->
<!--    <th>Recurrence</th>-->
<!--    <th>Algorithm</th>-->
<!--    <th>Big-Oh Solution</th>-->
<!--  </tr>-->
<!--  <tr>-->
<!--    <th>T(n) = T(n/2) + O(1)</th>-->
<!--    <th>Binary Search</th>-->
<!--    <th>O(log(n))</th>-->
<!--  </tr>-->
<!--  <tr>-->
<!--    <th>T(n) = T(n-1) + O(1)</th>-->
<!--    <th>Factorial</th>-->
<!--    <th>O(n)</th>-->
<!--  </tr>-->
  <!-- <tr> -->
  <!--  <th>T(n) = 2T(n/2) + O(1)</th> -->
  <!--  <th>tree traversal</th> -->
  <!--  <th>O(n)</th> -->
  <!-- </tr> -->
<!--  <tr>-->
<!--    <th>T(n) = 2T(n/2) + O(n)</th>-->
<!--    <th>Mergesort</th>-->
<!--    <th>O(n*log(n))</th>-->
<!--  </tr>-->
<!--  <tr>-->
<!--    <th>T(n) = T(n-1) + O(n) </th>-->
<!--    <th>bubble sort </th>-->
<!--    <th>O(n<sup>2</sup>)</th>-->
<!--  </tr>-->
<!--  <tr>-->
<!--    <th>T(n) = T(n-1) + T(n-2) + O(1)</th>-->
<!--    <th>fibonacci</th>-->
<!--    <th>O(2<sup>n</sup>)</th>-->
<!--  </tr>-->
<!--  </table>-->
	                      	                    

<!--####Recursion Trees (Drop!?!?!?!!!!!)-->

<!--The call stack is inherently tied to how a processor handles function calls. But algorithms don't always have to be implemented in functions! When we think of recursive algorithms, we can draw them as recursion "trees." -->

<!--<img src="https://users.soe.ucsc.edu/ ~fire/dev-2008f-12/labs/lab8-Recursion-vs-Iteration/fib_5.png" width=70% alt="recursion tree for fibonacci">-->

<!--Then, to calculate the time complexity of the algorithm, we look at the total work done in the tree. Here's a recursion tree for a recursive factorial algorithm with input 3:-->

<!--```-->
<!--    factorial(3)-->
<!--         |-->
<!--    factorial(2)-->
<!--         | -->
<!--    factorial(1)-->
<!--```-->
<!--The total work done for `factorial(3)` is the work done for factorial(1) + any extra work done to find factorial(2) from the factorail(1) answer, plus any extra work to find factorial(3) from the factorial(2) answer.  We know from looking at the factorial algorithm that the only extra work is multiplying each smaller answer by the number we're on.  For example, factorial(3) = 3* factorial(2).  And multiplicaiton happens to be one of those simple operations that we can almost always consider O(1). -->


<!--And here's one with input n:-->
<!--```-->
<!--    factorial(n)-->
<!--         |-->
<!--    factorial(n-1)-->
<!--         |-->
<!--    factorial(n-2)-->
<!--        ...-->
<!--    factorial(2)-->
<!--         |-->
<!--    factorial(1)-->
        
<!--```-->





###Discuss


<details><summary>Would our simple search algorithm work on an unsorted array?</summary>Yes!</details>

<details><summary>Would binary search work on an unsorted array?</summary>No! We wouldn't be able to reliably eliminate half of the array. </details>

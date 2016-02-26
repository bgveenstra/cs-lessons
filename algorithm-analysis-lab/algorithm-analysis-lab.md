# Algorithm Analysis Lab

1. Write a function called `compare` that compares two numbers. The function should return `1` if the first number is greater than the second, `0` if they are equal, or `-1` if the first number is less than the second.    

    How many calculations does your function do?
    What is the Big O time complexity of your function?


1. Write a function to find the middle element in an array.  How many calculations (including comparisons) does your function do for:   
    the input array [0,4,5]   
    an input array with 8 elements    
    any input array with `n` elements   

    What is the Big O time complexity of your function?

1. Write a function to find the maximum element in an array. What is the Big O time complexity of your function? Using Big O notation, how much extra space does your function require (not counting the space used for the input array)?

1. Write a function called `indexOf` that takes in a number and an array and searches for the number in the array. If the number is in the array, it should return the array index where it found the number. If the number is not in the array, it should return `null`.  What is the Big O time complexity of your function?

1. Write a function called `countNums` that takes in an array of numbers and counts how many times each number in the array appears.  What is the Big O time complexity of your function? Using Big O notation, how much extra space does your function require (not counting the space used for the input array)?


1. Write a function called `findShared` that takes in two arrays and outputs a new array that contains every number appearing in both input arrays. What is the Big O time complexity of your function? Using Big O notation, how much extra space does your function require (not counting the space used for the input array)?


## Sorting

There are many different possible approaches for sorting - different sorting algorithms. In this lab, you'll analyze and implement two different sorting algorithms: bubble sort and mergesort

### Bubble Sort

[First, some Hungarian ("Csángó") folk dance](https://www.youtube.com/watch?v=lyZQPjUT5B4)

Bubble sort is one of the first sorting algorithms you should try and master.  It essentially forces larger elements to 'sink' to the bottom/beginning while inadvertently 'floating' smaller elements to the top/end of a list.  This is done with numerous comparisons between one element in an array with its neighbor.  

####Sort the list using Bubble Sort: [5,4,2,3,1,6]

#####Iteration 1
Look at the first two elements in the list. Make sure they're in the correct order.
	
0: [**5, 4**,2,3,1,6]  

Is 5 > 4 ? Yes! Swap!

If an element on the left (5) is greater than the element on the right (4), the two elements 'swap' locations

1: [4,**5,2**,3,1,6]  

2: [4,2,**5,3**,1,6]  

3: [4,2,3,**5,1**,6]  

4: [4,2,3,1,**5,6**]  


**Important:** We now know that the last element in the list is the largest element in the list. There's no need to do a comparison with that number ever again.


#####Iteration 2

0: [**4,2**,3,1,5,~~6~~]

1:  [2,**4,3**,1,5,~~6~~]

2:  [2,3,**4,1**,5,~~6~~]

3:  [2,3,1,**4,5**,~~6~~]

Stop!

Remember: we know that last element is the largest number in the list.  There is no need to compare against that number ever again.  We also now know that the **second** to last number is the second largest number; no need to move that one ever again as well. (Detect a trend?)

#####Iteration 3

0: [**2,3**,1,4,~~5,6~~]  

If an element on the left has met a larger or equal element, we look at its bigger neighbor and now compare the larger neighbor to it's neighbor on the right.  The process is continued until we reach the numbers we know are already sorted.

1: [2,**3,1**,4,~~5,6~~]

2: [2,1,**3,4**,~~5,6~~]

Stop!

We don't stop checking pairs of numbers until we hit the already-sorted section.  

#####Iteration 4

0: [**2,1**,3,~~4,5,6~~]

1: [1,**2,3**,~~4,5,6~~]

Stop!

#####Iteration 5
0: [**1,2**,~~3,4,5,6~~]

Stop!


#####Iteration 6

0: [**1**, ~~2, 3, 4, 5, 6~~]


When there is only one element (the first element) left in our unsorted list, it is already sorted for us as a freebie!

#####List is now sorted using Bubble Sort: [1,2,3,4,5,6]

![](http://cdn2.crunchify.com/wp-content/uploads/2013/01/BubbleSort-Algorithm-Crunchify.jpg)

####Bubble Sort Analysis

Work with a partner to write pseudocode for bubble sort!

#####Hints:
If you want to swap two variables, a and b, it's easiest to use a temporary variable:

```javascript
var a, b, temp;
temp = a;
a = b;
b = temp;
```



###Merge Sort

Merge sort is the first powerful sorting algorithm that you will encounter in the wilds of the real world (baked into Safari and Firefox.)  It uses an extremely efficient application of the 'Divide and Conquer' approach.

Merge Sort works on the basic principal of dividing your list into sub-lists (recursively) until your sub-lists are of length one or zero.  Once your sub-lists are at that size, you merge with a neighboring sub-list.  When you merge them, you merge them in ascending or descending order, depending on your implementation.  

![Merge Sort visualization](https://webdocs.cs.ualberta.ca/~holte/T26/Lecture6Fig6.gif)

There are TWO functions that work together to accomplish a Merge Sort:

-  A `mergeSort` function that takes an array, splits the array in two, and calls a `merge` function.  The `mergeSort` function **is recursive**.  

-  A `merge` function that takes two arrays as parameters, looks at the the first elements of the two lists, and assembles a resulting list based on the two lists 'zipped' together by pushing the lowest to highest valued elements. The `merge` function **is not recursive**.

####Make your own Mergesort implementation!
Create a mergeSort that will sort a list of student names from this class!


<!--
---
title: Computer Architecture
type: lesson
duration: "1:15"
creator:
    name: 
    city: SF
competencies: Computer Science

@TODO - copyright for images (or replace)
---


Parts of a computer  
Memory  
Care because processor accesses values from memory (what's an array? a linked list?!!)  
Processor, Instructions, Processor Registers and Cache  
Processes, Threads  
Machine language, compiling  
Virtual Machines, Interpreters  
Interpreters - variable hoisting  ?



Get a one-sentence understanding of the parts that aren't relevant to web dev but that you'll be expected to know.  Define key terms and/or identify key properties of a language, especially the ones we've used in class.


---
References:
http://www.bbc.co.uk/education/guides/zwbk87h/revision/1
https://www.recurse.com/blog/7-understanding-c-by-learning-assembly
---

-->

# Computer Architecture

### Objectives
*After this lesson, students will be able to:*

- Describe how computers store and process information.   
- Manipulate binary data.   
- Describe how programs are internally converted to instructions that a computer can carry out.   
- Use appropriate technical terms for categories of programming languages, and apply these terms to JavaScript and Ruby.  

### Preparation
*Before this lesson, students should already be able to:*

- Predict the result of logical operations (AND, NOT, OR) on boolean values. 
- Create and run programs in JavaScript or Ruby. 
- Distinguish among different data types. 


## Computers 

Modern computers take in instructions and data and perform calculations on the data according to the instructions.  To accomplish this, computers have four basic parts:

* input devices - so the computer can accept outside information (keyboard, mouse)
* memory - so the computer can store information including instructions (hard drive, usb stick, solid state disk)
* processor - so the computer can carry out instructions and run calculations on data (CPU)
* output devices - so the computer can return results (printer, monitor)

![computer block diagram - input, output, and memory connected to processor](http://onlinemca.com/mca_course/kurukshetra_university/semester1/c/img_c/comp_block_diagram.png)


You're already familiar with a few input and output devices. If you've shopped for a computer recently, you've also heard information about computers' memory and processor specifics in product information. 




## Memory

### Bits and Binary Notation

Computers store information in binary notation, as series of `1`s and `0`s called bits.  Think about what how much information one bit can hold.  

Pair up and discuss: 

1. ... would you be able to tell someone whether you walked to class this morning with only bit (one `0` or `1`)? 

1. ... could you tell someone your birthday with only one bit? 

<details>   
  <summary>How many different answers or alternatives can one bit represent?</summary>   
   <p>Two! You may have come up with some cool schemes to pass information.  Remember computers aren't as clever as people! From a computer's perspective, one bit can only represent two possibilities. </p>   
</details>   


Because bits don't hold much information, programmers think about them in groups.  "Bytes" are groups of 8 bits, like `01000111` and `01000001`.

<!--<details> -->
<!--  <summary>How many different combinations of `1`s and `0`s are possible in a byte?</summary>-->
<!--   <p> 2<sup>8</sup>, or 256</p>-->
<!--</details> -->

ASCII encoding uses seven bits to represent each character. That only allows for 128 different codes, meaning 128 different characters. Digits and English letters take up half that!  Because of ASCII's limited range, it's been replaced by encodings that can use more bits to represent each character, like UTF-8 (which you've probably written many times in your HTML - `<meta charset="UTF-8">`).  UTF-8 can encode languages that aren't English! Yay!

![ASCII encoding table](http://web.alfredstate.edu/weimandn/miscellaneous/ascii/ASCII%20Conversion%20Chart.gif)


**Bonus: Hexadecimal Notation**

The ASCII table above also has a column for the HEX or "hexadecimal" value associated with each character. The digits used for hexadecimal notation are [`0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8`, `9`, `A`, `B`, `C`, `D`, `E`] which correspond to decimal values of 0 through 15. 


<details>
<summary>Where have you seen hex values used before?</summary>
<p>One possibility is for hex color values in CSS</p>
```css
body {
	color: "#ED86B4";
}
```
</details>

Binary, hexadecimal, and our normal decimal representations are all just different ways to look at the same numbers you're already familiar with.  If you'd like to learn more about this topic, it'll help to know that our normal decimal numbers are "base 10," binary numbers are "base 2," and hexadecimal numbers are "base 16." Octal numbers are less common. 

<details>
<summary>Just for fun... can you tell from the chart what the "base" of the octal numbers (in the OCT column) might be?</summary>
<p>Octal numbers are base 8. The "base" of a number system tells how many digits it has. Looking at the chart, you'll notice the OCT column only uses the digits 0 through 7 -- 8 digits!</p>
</details>

<!--#### Practice with Binary Numbers-->


<!--Bit manipulation describes operations that act on binary numbers.  You can perform common arithmetic on binary numbers. There's also a specail name for "bit shifting" values left or right. This either adds a `0` at the end of the number for left shift ( `<<`), which is equivalent to multiplying by 2, or removes the last binary digit for right shift (`>>`), which is almost like diving by two (why almost?).  -->

<!--As sequences of 0s and 1s, binary numbers can also be acted on by logical operators, if you consider each `1` like a `true` and each `0` like a `false`.  For example, `NOT 101` would give `010`.   `1011 AND 1101` would give `1001`. -->

<!--<details> -->
<!--  <summary>What other operations do you think can act on binary numbers?</summary>-->
<!--   <p> We've seen `AND` and `OR`.</p>-->
<!--</details> -->

<!--A boolean operator you may not know of is `XOR`. It's a lot like `OR`, except `a XOR b` is only true if exactly one of a or b is true.  If both a and b are true, or if both are false, `a XOR b` is false.   So `1010 XOR 0011` would give `1001`.-->

### Memory: Where Bits Live

All of the bits of data and instructions your computer uses are stored in what's called the computer's "memory."  That's important to realize - every peice of information used in calculations, and the instructions the computer uses for the calculations themselves, are stored in the computer's memory. The actual act of doing those calculations happens in the processor, but all of the information required has to exist in memory first. We'll talk more about the processor in a few minutes.

There are different kinds of memory, which mostly influence fiscal cost of the memory and how quickly the computer can access data stored on them. 

![chart of memory types: size, cost, and access speed](https://cloud.githubusercontent.com/assets/3254910/12181035/b55fae34-b534-11e5-8f86-18b111d0b3ef.png)  

Lower levels usually provide more storage and cost less per unit of space, but for each level lower, time required to access data stored in that level increases. Reading or writing to a hard disk can be orders of magnitude slower than reading or writing "from memory".  With current technology, it can be faster to get data from a different computer in a local network (or even over the internet) than to read from a hard disk. 

 Most modern personal computer hard drives can store hundreds of gigabytes or even a few terabytes, and most RAM is sold in 4-, 8-, or 16-gigabyte "sticks."

* A single character can be stored in a byte or two of memory. 
* A small text file is often a few kilobytes long.  
* An average music MP3 file would be a few megabytes.
* DVDs are usually a few gigabytes.  
* A terabyte is enough to hold about 2000 hours of good quality audio.  
* A petabyte is about three month's worth of tweets - for everyone using twitter!  

<img src="http://www.oceantechonline.com/wp-content/uploads/2013/04/hard-drive1.png" alt="hard disk drive" width="25%">

<img src="http://www.nemixcorp.com/media/catalog/product/cache/1/image/9df78eab33525d08d6e5fb8d27136e95/1/8/184_pin_eccx2-a.jpg" width="30%">


You can think of your computer's memory as a giant city - in fact, we refer to the location in memory where some information is stored as that information's memory address. When you create a variable, some amount of space in memory is reserved for that variable; this is called memory allocation. When a variable is no longer needed, the space should be freed; this is called deallocation.  Most high-level programming lanaguages handle memory allocation and deallocation for us. Programming lanaguges that automatically handle getting rid of old data (for instance, after it goes out of scope) are doing "garbage collection" for us.  


## Processors

<img src="https://blazotech.files.wordpress.com/2011/05/1298865422-79.jpg" width="25%">

Bits are transfered through the computer to support even the most basic of operations. In memory, they represent the data programs act upon as well as the programs themselves!  None of this information really has any effect until it's processed by a computer's processor(s). The processor is the brain of the computer.

Processors perform all of the operations that take place within your computer according to a set of instructions.  A processor is just a small group of computer chips. You can think of the processor as having a few main important parts:

 * the arithmic logic unit performs operations
 * the registers are tiny storage spaces for the data beging operated on
 * the cache is another small area of memory for data that's likely to be accessed again soon. 


<details>   
  <summary>How many different combinations of `1`s and `0`s are possible in a 32-bit word?</summary>   
   <p> 2<sup>32</sup>, or 4294967296</p>   
</details>   


The number of bits a processor can work on at one time is related to its "word size." Common word sizes are 32 bits or 64 bits, which is why you'll mostly hear about 32bit or 64bit processors.  


### Processes and Threads 

Each instance of a running program is called a process; a processor can only work on one process at once. To see a list of processes running on your computer, enter the `top` command in your terminal. 

A single processor can only work on one thing at a time. Users want to be able to do more than one thing at a time with their computers. There are a few approaches to fixing this problem. First, the processor changes which process it's working on avoid any downtime. If one process needs to wait for user input, for example, the computer will work on a different process for a while to fill that time.  Many computers also have "dual" or "quad" core processors, which is like having 2 or 4 processors. Most modern architectures also allow for threading, where process are divided into smaller "threads", individual tasks that the processor focuses on for a short amount of time.



## Break!


## Interpreters and Compilers

If the computer works with 0s and 1s, how does it  know what to do when we give it a line of code like `var speed = 0;`?


Very early in the history of computer development, Assembly languages were created to manipulate computer memory and operations in a way that's possible for humans to read, instead of just 1s and 0s.  How human-readable they are depends on your level of training. There is usually a one-to-one correspondance between a line of code in assembly and an operation carried out by the machine, so they still look a lot like code and not at all like English.

Here's an example of some assembly commands and debugging information. The debugging information on the left hand side includes the name of the file that was run (`test`) and the memory address where the beginning of the function started. The assembly commands are in the middle, between the colons and the semicolons. The parts after the colons are comments.

```assembly
test`main:
test[0x100000f90] <+0>: pushq  %rbp         ; these first two instructions keep track of  
test[0x100000f91] <+1>: movq   %rsp, %rbp   ;  ... where the function starts
test[0x100000f94] <+4>: xorl   %eax, %eax   ; does a logical XOR on the same thing twice - whatever's stored in %eax
					    ;  ... and stores the result in %eax - ensuring %eax is now 0
					    ;  ... the l in xorl just stands for "long" integer data type
test[0x100000f96] <+6>: popq   %rbp	    ; pops the stored value of the base pointer back into the base pointer
test[0x100000f97] <+7>: retq                ; jumps back to the return address (which was also stored in call stack)
```


Can you identify what the code is doing?  The %rbp, %rsp, and %eax are registers - data storage locations directly in the CPU. It's very fast for a computer to access the processor's registers, and they usually store the operands for an arithmetic or logic operation being carried out. The %rbp and %rsp registers have special purposes; they help the computer keep track of where in the call stack the current operations are being carried out (we won't go into this too much, but it's the basis for how control flow works).


Here's that code translated into a low-level programming language called C:

```c
/* test.c */
int main(){
  int a = 16;
  int b = 32;
  return 0;
}
```

What do you think is happening in the code samples above? What do you think `int` means? What data types are x, y, and main?

Here's a JavaScript analogue:

```js
(function main(){
  var a = 16;
  var b = 32;
  var c = a + b;
  return c;
})()
```


## Compilers and Interpreters

Compiling translates source code into a lower-level language, usually into an assembly language or machine code that can be run directly by the processor. Programming in a compiled language requires an extra step between writing and running code; you literally have to compile the code into a language the machine can read.  This creates extra delay as you have to compile code before running it, but the compiled code runs very fast because the machine can run it very directly. 

With interpreted languages like we've been using, the source code is translated a little at a time in real time as it's run, instead of all at once before it is run.  The code isn't translated directly all the way down to the machine code level. It's translated to an intermediate format and then run in a virtual machine -- a simulated computer within the actual computer. The virtual machine has precompiled chunks of code that map to machine code.  

Programmers working with compiled languages have to use different compilers for the different systems they work on - Windows, Ubuntu, and OS X, for example. They have to consciously find and use the correct compiler.   When working with interpreted languages, the same code can run on many systems. The effort of translating that code to machine language falls to the virtual machine, where the programmer doesn't have to worry about it at all.

One popular compiled language used in web development is Java. 

## Static and Dynamic Typing

When a language makes you specify the type of a variable and does not allow you to change it, that's called static typing.  We haven't had to specify the types of variables in JavaScript or Ruby, and we can change the type of a variable - this is dynamic typing! Interpreted and compiled languages can both be statically or dynamically typed.

## Practice

Discuss the following questions with a partner:

1. Is JavaScript "garbage collected"?  How about Ruby?

1. Does JavaScript have "static typing" or "dynamic typing"?  Ruby?

1. Is JavaScript a "compiled language" or an "interpreted language"? What about Ruby?

1. What is a "scripting lanauage"? Give an example.

1. What do we mean by "high-level" and "low-level" languages? Give an example of each. 

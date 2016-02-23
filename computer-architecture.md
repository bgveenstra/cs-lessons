---
title: Computer Architecture
type: lesson
duration: "1:25"
creator:
    name: 
    city: SF
competencies: Computer Science

---


<!--

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

## Intro (5 minutes)

### Objectives
*After this lesson, students will be able to:*

- Describe how computers store and process information.   
- Explain how data is encoded in binary or hex formats and where these formats are used. 
- Distinguish between compilers and interpreters, and describe how each converts programs into instructions that a computer can carry out.
- Use appropriate technical terms for categories of programming languages, and apply these terms to JavaScript and Ruby.  

### Preparation
*Before this lesson, students should already be able to:*

- Predict the result of logical operations (AND, NOT, OR) on boolean values. 
- Create and run programs in JavaScript or Ruby. 
- Distinguish among different data types.
- Define "high-level" and "low-level" in a development context. 


## Basic Parts of Computers

Modern computers take in instructions and data and perform calculations on the data according to the instructions.  To accomplish this, computers have four basic parts:

* input devices - so the computer can accept outside information (keyboard, mouse)
* memory - so the computer can store information including instructions (hard drive, usb stick, solid state disk)
* processor - so the computer can carry out instructions and run calculations on data (CPU)
* output devices - so the computer can return results (printer, monitor)

![computer block diagram - input, output, and memory connected to processor](http://onlinemca.com/mca_course/kurukshetra_university/semester1/c/img_c/comp_block_diagram.png)


You're already familiar with a few input and output devices. If you've shopped for a computer recently, you've also heard information about computers' memory and processor loadouts. 


## Bits, Binary Notation, and Encoding (10 minutes)

Let's look at **how the computer "sees" and stores information**.

Computers store information in binary notation, as series of `1`s and `0`s called bits.  Think about what how much information one bit can hold.  

Pair up for 1 minute and discuss: 

1. ... would you be able to tell someone whether you walked to class this morning with only bit (one `0` or `1`)? 

1. ... could you tell someone your birthday with only one bit? 

--


<details>   
  <summary>How many different answers or alternatives can one bit represent?</summary>   
   * Two! You may have come up with some cool schemes to pass information.  Remember computers aren't as clever as people! From a computer's perspective, one bit can only represent two possibilities.  
</details>   


Because bits don't hold much information each, programmers think about them in groups.  "Bytes" are groups of 8 bits, like `01000111` and `01000001`.


###Information Encoding  (10 minutes)

So how many bits would it take to tell someone your birthday? Or what color each pixel in an image should be? Or what  letter should appear on your website next? These are the basic questions behind "encoding." One bit isn't enough, but text and numbers can be encoded in a computer as *patterns* of binary digits.  You may have heard of ASCII encoding, often used for ASCII art:

```
  '___'
  ( O.O)
/(,,,,,)      // This is definitely an owl.
   ^ ^
   
```

ASCII encoding uses seven bits to represent each character. That only allows for 128 different codes, meaning 128 different characters. Digits and English letters take up half that! Punctuation marks, whitespace, and special control characters are most of the rest.  It's not worthwhile to memorize ASCII encodings, but the table below is numbered in our normal decimal notation. It can give you a good idea how to count in binary notation and in another notation called "hexadecimal" or "hex" for short.


![ASCII encoding table](http://web.alfredstate.edu/weimandn/miscellaneous/ascii/ASCII%20Conversion%20Chart.gif)

####Optional: Hexadecimal Notation

The ASCII table above also has a column for the HEX or "hexadecimal" value associated with each character. The digits used for hexadecimal notation are [`0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8`, `9`, `A`, `B`, `C`, `D`, `E`] which correspond to decimal values of 0 through 15. 

<details>
	<summary>Where have you seen hex values used before?</summary>
	<p>One possibility is for hex color values in CSS:</p>
	```css
	body {
		color: "#ED86B4";
	}
	```
</details>

### ASCII vs UTF-8

128 different codes aren't nearly enough for all of the characters on modern websites. Because of ASCII's limited range, it's been replaced by encodings that can use more bits to represent each character, like UTF-8. You've probably mentioned UTF-8 many times in your HTML document head tags: `<meta charset="UTF-8">`.  UTF-8 uses variable numbers of bits to encode different characters. So in UTF-8, "J" is `&#x4A;` (in hexadecimal), and  "&#x266b;" is `&#x266b;`.  With the freedom yo use extra bits, UTF-8 can encode symbols (cool!) but also languages that aren't English (essential!).



<!--**Bonus: Numerical "Bases"**-->

<!--Binary, hexadecimal, and our normal decimal representations are all just different ways to look at the same numbers you're already familiar with.  If you'd like to learn more about this topic, it'll help to know that our normal decimal numbers are "base 10," binary numbers are "base 2," and hexadecimal numbers are "base 16." Octal numbers are less common. -->

<!--<details>-->
<!--<summary>Just for fun... can you tell from the chart what the "base" of the octal numbers (in the OCT column) might be?</summary>-->
<!--<p>Octal numbers are base 8. The "base" of a number system tells how many digits it has. Looking at the chart, you'll notice the OCT column only uses the digits 0 through 7 -- 8 digits!</p>-->
<!--</details>-->

<!--  > #### Practice with Binary Numbers-->


<!-- > Bit manipulation describes operations that act on binary numbers.  You can perform common arithmetic on binary numbers. There's also a specail name for "bit shifting" values left or right. This either adds a `0` at the end of the number for left shift ( `<<`), which is equivalent to multiplying by 2, or removes the last binary digit for right shift (`>>`), which is almost like diving by two (why almost?).  -->

<!-- > As sequences of 0s and 1s, binary numbers can also be acted on by logical operators, if you consider each `1` like a `true` and each `0` like a `false`.  For example, `NOT 101` would give `010`.   `1011 AND 1101` would give `1001`. -->

<!-- > <details> -->
<!-- >  <summary>What other operations do you think can act on binary numbers?</summary>-->
<!-- >   <p> We've seen `AND` and `OR`.</p>-->
<!-- > </details> -->

<!-- > A boolean operator you may not know of is `XOR`. It's a lot like `OR`, except `a XOR b` is only true if exactly one of a or b is true.  If both a and b are true, or if both are false, `a XOR b` is false.   So `1010 XOR 0011` would give `1001`.-->




<!-- > <details> -->
<!-- >   <summary>How many different combinations of `1`s and `0`s are possible in a byte?</summary>-->
<!-- >   <p> 2<sup>8</sup>, or 256</p>-->
<!-- > </details> -->

##Memory (5 minutes)

All of the bits of data and instructions your computer uses are stored in what's called the computer's "memory."  That's important to realize - every piece of information used in calculations, and the instructions the computer uses for the calculations themselves, are stored in the computer's memory. 

You can think of your computer's memory as a giant city - in fact, we refer to the location in memory where some information is stored as that information's "memory address."

### Main Types of Memory

Some information in a computer's memory persists after the computer is turned off; this is mostly stored on the hard disk drive or ssd. Solid state disks (SSDs) are faster than hard disks because hard disks literally have to wait for a disk to spin into the right position to read or write data!  These persistent memory stores are like the computer's "long-term" memory.

<img src="http://www.oceantechonline.com/wp-content/uploads/2013/04/hard-drive1.png" alt="hard disk drive" width="25%">
*a hard disk drive - data stored here persists when the computer is restarted*

Some kinds of memory clear their information when the computer is turned off. The example talked about most often is RAM, which stands for "random access memory."  That's the computer's "short-term memory." It's faster for a computer to access information from RAM than from either a hard disk drive or ssd.

<img src="http://www.nemixcorp.com/media/catalog/product/cache/1/image/9df78eab33525d08d6e5fb8d27136e95/1/8/184_pin_eccx2-a.jpg" width="30%">
*sticks of RAM - not persistant memory*

<!--<details>-->
<!--<summary> Do you think the following are stored "on disk" or in RAM: the code for your computer's operating system, an array you create in the Chrome developer tools console, a file you download?</summary>-->
<!--<ul>-->
<!--<li>The code for your operating system had better persist after you restart your computer! That should be on disk.</li>-->
<!--<li>An array you create in the Chrome developer tools won't even be there if you restart Chrome. It must be stored in RAM. </li>-->
<!--<li>A file you download will be there the next time you start your computer, so it must be stored on disk. </li>-->
<!--</ul>-->

<!--</details>-->


Most modern personal computer hard drives can store hundreds of gigabytes or even a few terabytes, and most RAM is sold in 4-, 8-, or 16-gigabyte "sticks."  

**Memory Size Requriements**
	
	* A single character like "J" or "&#x266b;" can be stored in a few bytes of memory. 
	* A small text file is often a few kilobytes long.  
	* An average music MP3 file would be a few megabytes.
	* DVDs are usually a few gigabytes.  
	* A terabyte is enough to hold about 2000 hours of good quality audio.  
	* A petabyte is about three month's worth of tweets - for everyone using twitter!  


### Memory Allocation and Deallocation

When you create a variable, some amount of space in memory is reserved for that variable, a place in the memory "city" where that information can live.  This is called memory allocation. When a variable is no longer needed, the space should be freed; this is called memory deallocation. Most high-level programming languages handle memory allocation and deallocation for us. 

<!--> Programming lanaguges that automatically handle getting rid of old data (for instance, after it goes out of scope) are doing "garbage collection" for us.  -->

<!-- > <details>-->
<!-- > <summary>Is JavaScript garbage collected?</summary>-->
<!-- > <p>We've created JavaScript variables, but we haven't had to carefully destroy them when we're done using them.  JavaScript **is** a garbage collected language.</p>-->
<!-- > </details>-->





## Processors (10 minutes)


Processors perform all of the operations that take place within your computer.  The processor is the "brain" of the computer!

<img src="https://blazotech.files.wordpress.com/2011/05/1298865422-79.jpg" width="25%"> 
*a processor*


 You can think of the processor as having a few main important parts:

 * the arithmetic logic unit, which performs arithmetic and logical operations on binary data
 * the registers, which are tiny storage spaces for the data beging operated on
 * the cache, which is another small area of memory for data that's likely to be accessed again soon


The number of bits a processor can work on at one time is related to its "word size." Common word sizes are 32 bits or 64 bits, which is why you'll mostly hear about 32bit or 64bit processors.  



<!-- > <details>   -->
<!-- >  <summary>How many different combinations of `1`s and `0`s are possible in a 32-bit word?</summary>   -->
<!-- >   <p> 2<sup>32</sup>, or 4294967296</p>   -->
<!-- > </details>   -->


Processors act on data stored in memory and follow instructions stored in memory. Where that information is stored has an impact on how quickly the processor can access and act on it.

![chart of memory types: size, cost, and access speed](https://cloud.githubusercontent.com/assets/3254910/12181035/b55fae34-b534-11e5-8f86-18b111d0b3ef.png)  


### Processes and Threads 

Each instance of a running program is called a process; a processor can only work on one process at once. To see a list of processes running on your computer, enter the `top` command in your terminal. Seriously, do it now.

A single processor can only work on one thing at a time. Users want to be able to do more than one thing at a time with their computers! There are a few approaches to fixing this problem.  A processor changes which process it's working on avoid any downtime. If one process needs to wait for user input, for example, the computer will work on a different process for a while to fill that time.  Many computers also have "dual" or "quad" core processors, which is like having 2 or 4 processors. Most modern architectures also allow for threading, where process are divided into smaller "threads", individual tasks that the processor focuses on for a short amount of time.


## Interpreters and Compilers

If the processor works with 0s and 1s, how does it know what to do when we give it a line of code like `var speed = 50;`? The code we write has to be translated to instructions the processor can carry out. 


### Low-level Programming Languages (5 minutes)

A lot of work of computer science since the mid-1900s has focused on letting humans write human-readable code.  Assembly languages are very low-level programming languages. This means it's very close to machine code; it's a slightly more readable layer just on top of 1s and 0s. There is usually exactly one command in assembly for every possible operation the processor can do. 

Here's an example of some assembly commands:

<!--```assembly-->
<!--; memory address        ; assembly command & operands-->
<!--test[0x100000f90] <+0>: pushq  %rbp         -->
<!--test[0x100000f91] <+1>: movq   %rsp, %rbp   -->
<!--test[0x100000f94] <+4>: xorl   %eax, %eax  -->
<!--test[0x100000f96] <+6>: popq   %rbp	    -->
<!--test[0x100000f97] <+7>: retq                -->
<!--```-->

```assembly
PUSHQ    %rbp
MOVQ     %rsp, %rbp
XORL     %eax, %eax
POPQ     %rbp
RETQ
```

The first two lines keep track of where the funciton starts. Then the next line sets the value of the %eax processor register to 0.  Finally, the last two lines cause the processor to return.

<!--Can you guess what the code is doing?  The %rbp, %rsp, and %eax are registers - data storage locations directly in the processor. It's very fast for a computer to access the processor's registers, and they usually store the operands for an arithmetic or logic operation being carried out. The %rbp and %rsp registers have special purposes; they help the computer keep track of where in the call stack the current operations are being carried out (we won't go into this too much, but it's the basis for how control flow works).-->


Assembly languages are basically the lowest level languages possible.  Below is some very similar code expressed in a programming language called C. 

```c
int main(){
  int x = 8; // this line didn't happen in the assmebly!
  return 0;
}
```

Line by line, what do you think is happening in the C code sample above? 

<details>
  <summary>What do you think `int` means?</summary>
  In C, `int` stands for "integer." It specifies the type of the new `x` variable.
</details> 

<details>
  <summary>What data types are `x` and `main`?</summary>
  `x` is an integer, and `main` is a function. In C, we specify the "return type" of a function, which is why it's defined as `int main` instead of `def main` or `function main`.
</details> 

### Compiled Languages (10 minutes)

C came after assembly languages and was specifically designed to be easier for humans to read. It's a higher-level programming language than assembly, but it's still possible to translate it pretty directly to processor instructions. In fact, C is translated into assembly before it's run. This means C is a "compiled language."   Compiling translates code from a higher-level language into a lower-level language, usually into an assembly language that can be run directly by the processor. Programming in a compiled language requires an extra step between writing and running code; you have to use a program called a compiler to compile your code before running it.  This creates extra delay, but the compiled version of the code runs fast because all the instructions are exactly as the processor expects. 

One popular compiled language used in web development is Java, which compiles to a special "bytecode" instead of to assembly. 

### Interpreted Languages (10 minutes)

JavaScript and Ruby are "interpreted languages." For interpreted languages, the source code still has to be translated so the computer can run it.  However, the source code is translated a little at a time as it's run, instead of all at once before it is run.  Also, the code isn't translated directly all the way down to the machine code level. It's translated to an intermediate format and then run in a virtual machine -- a simulated computer within the actual computer. The virtual machine has precompiled chunks of code that map to assembly code.  The way an interpreter is written can have a big impact on how a language works -- this is why we have variable hoisting in JavaScript, for example!

Programmers working with compiled languages have to use different compilers for the different systems they work on - Windows, Ubuntu, and OS X, for example. They have to consciously find and use the correct compiler.   When working with interpreted languages, the same code can run on many systems. The effort of translating that code to machine language falls to the virtual machine, where the programmer doesn't have to worry about it at all.

For more information on compiled and interpreted languages, check out the wikipedia articles on each!

## Static and Dynamic Typing (5 minutes)

C is a statically typed language, meaning it makes sure types match (for operations like "hello" + 5) when the code is compiled. If you tried to compile a C file with `"hello" + 5` in it, the compiling step would give you an error. You wouldn't even be able to get to the stage where you try to run it.  Most statically types languages make you specify the type of a variable and do not allow you to change it. Languages with dynamic typing only check types at runtime.  So in Ruby you'd get `TypeError: no implicit conversion of Fixnum into String` when you tried to *run* the code. 

Here's one way that C function from before might be written in Ruby:

```ruby
def main
  x = 8
  0
end
```


## Practice (20 minutes)


1. How many different values can you represent with one bit?  One decimal digit? One letter?  

1. How many different values can you represent with a byte?  How about with a sequence of eight letters?

1. What do we mean by "high-level" and "low-level" languages? Give an example of each. 

1. What is a "scripting lanauage"? Give an example.

1. Does JavaScript have "static typing" or "dynamic typing"? 

1. Is JavaScript a "compiled language" or an "interpreted language"? What about Ruby?  What does this mean for us as JavaScript and Ruby developers?

1. How might you explain the fact that in JavaScript `"hello" + 5` is `"hello5"`?

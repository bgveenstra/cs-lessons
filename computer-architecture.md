---
title: Computer Architecture
type: lesson
duration: "1:15"
creator:
    name: Brianna Veenstra
    city: SF
competencies: Computer Science

@TODO - check copyright of images
---

# Computer Architecture

### Objectives
*After this lesson, students will be able to:*

- Explain how computers store information and how programs manipulate data stored in memory.   
- Manipulate binary and hexidecimal data.   
- Explain how programs are converted to binary instructions that a computer can read and carry out.   
- Categorize computer programming languages along common feature lines.  

### Preparation
*Before this lesson, students should already be able to:*

- Do basic arithmetic operations by hand and programatically.  
- Carry out the process of writing and running a script in JavaScript or Ruby.  


## Memory (20 mins)

### Bits 

Computers store information in binary notation, as series of bits.  The value of each bit can be `1` or `0`.  You can't convey much information with only one bit, so programmers often think about groups of bits.  Bytes are groups of 8 bits, like `01000111` and `01000001`. 


<details> 
  <summary>How many different combinations of `1`s and `0`s are possible in a byte?</summary>
   <p> 2<sup>8</sup>, or 256</p>
</details> 

ASCII encoding uses one byte to represent each character. Due to its limited range, it's been replaced by encodings that can use more bits to represent each character, like UTF-8 (which you've probably written many times in your HTML - `<meta charset="UTF-8">`)

_Bit manipulation describes operations that act on binary numbers, like shifting values right or left, which is equivalent to multiplying or dividing by 2._

#### Optional: Practice with Binary Numbers


### Where the Bits Live

Bits are transfered through the computer to support even the most basic of operations. We usually think of information as being stored in a computer's memory, but it's also processed in the computer's processor(s). There are also levels of memory: the processor's tiny but lightning-fast memory store, the cache, Random Access Memory, a hard drive (what is usally listed as "memory" in a computer's specs), and any external drives. The lower levels usually provide more storage and cost less per unit of space, but for each level lower, time required to access data stored in that level increases. Reading or writing to a hard disk can be orders of magnitude slower than reading or writing "from memory".  
 
![chart of memory types: size, cost, and access speed](https://cloud.githubusercontent.com/assets/3254910/12181035/b55fae34-b534-11e5-8f86-18b111d0b3ef.png)   

Processors interact with data in places called "registers" and in chunks called "words". The size of words a processor processes is an important part of computer architecture. Common word sizes are 32 bits or 64 bits, which is why you'll mostly hear about 32bit or 64bit processors.   

Modern processors usually allow threading, which has tasks trade off time using the processor. The processor is a bit like a chess pro playing multiple opponents at once - each game is a thread. 


Another statistic you'll usually hear about new computers is the amount of space they have in their hard drives, in terms of gigabytes.   


<details>   
  <summary>How many different combinations of `1`s and `0`s are possible in a 32-bit word?</summary>   
   <p> 2<sup>32</sup>, or 4294967296</p>   
</details>   



## How Code Runs

- Interpreter/compiler  
- Ruby interpreter vs JavaScript interpreter (hoisting)   

Interlude: things you should know about the languages you're using:   
	- static vs dynamic typing   
	- compiled/interpreted/just in time compiled   
	- 

If the computer works with 0s and 1s, how does it  know what to do when we give it a line of code like `var speed = 0;`?

Very early in the history of computer development, Assembly languages were created to manipulate computer memory and operations in a way that's possible for humans to read, instead of just 1s and 0s.  How human-readable they are depends on your level of training. 

There is usually a one-to-one correspondance between a line of code in assembly and an operation carried out by the machine.  

Assembly languages have to match the kind of hardware your computer has.  In particular, you need to know the computer's architecture (x86 is very common). Of course you also need to know the operating system. Here's an example of some assembly commands and debugging information. The assembly is on the right side of each line, after the colons.

```assembly
test`main:
test[0x100000f90] <+0>: pushq  %rbp
test[0x100000f91] <+1>: movq   %rsp, %rbp
test[0x100000f94] <+4>: xorl   %eax, %eax
test[0x100000f96] <+6>: popq   %rbp
test[0x100000f97] <+7>: retq
```

```assembly
add`main:
add[0x100000f90] <+0>:  pushq  %rbp
add[0x100000f91] <+1>:  movq   %rsp, %rbp
add[0x100000f94] <+4>:  movl   $0x30, %eax
add[0x100000f99] <+9>:  popq   %rbp
add[0x100000f9a] <+10>: retq  
```


Can you identify what the code is doing? Does it help to know that some Assembly language code instructions act directly on memory addresses?


Here's that code translated into a low-level programming language called C:

```c
/* test.c */
int main(){
  int a = 16;
  int b = 32;
  return 0;
}
```

```c
/* add.c */
int main(){
  int a = 16;
  int b = 32;
  return a + b;
}
```

What do you think is happening in the code samples above? What do you think `int` means? What data types are x, y, and main?

Here's a JavaScript analogue:

```js
(function main(){
  var a = 16;
  var b = 32;
  return 0;
})()
```


## Compiled vs Interpreted Languages

Compiling translates source code into a lower-level language, usually into machine code that can be run directly by the processor. Programming in a compiled language requires an extra step between writing and running code; you literally have to compile the code into a language the machine can read.  This creates extra delay as you have to compile code before running it, but the compiled code runs very fast because the machine can run it very directly. 


With interpreted languages like we've been using (JavaScript, Ruby), the source code is translated a little at a time in real time as it's run, instead of all at once before it is run.  The code isn't translated all the way down to the machine code level; it's run in a virtual machine -- a simulated computer within the actual computer. The virtual machine has precompiled chunks of code that map to other things. 



## Independent Practice (20 minutes)

  - bit manipulation?  
  - scalability coding challenge / large arrays  
  - some sort of logging  

## Conclusion (5 mins)
- Ask some questions
- See if anyone learned what they were supposed to
- See if you did a good job by teaching them stuff
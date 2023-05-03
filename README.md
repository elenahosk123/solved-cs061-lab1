Download Link: https://assignmentchef.com/product/solved-cs061-lab1
<br>
Today’s lab will get you set up, and cover the basics of how to use the LC3 Assembler/emulator, and write a tiny program in LC-3 Assembly language.

<em>The specs for today’s lab are rather lengthy, as there are a lot of new ideas &amp; activities to cover. </em>

<em>But don’t panic – each step is pretty simple, and most future lab specs will be shorter (but harder!) </em>

<h1>2      Objectives for This Week</h1>

<ol>

 <li>Set up remote access to your CS account on the server bolt.cs.ucr.edu 2. Introduction to the basics of LC3 programming</li>

 <li>Exercise 0: Hello World!</li>

 <li>Exercise 1: Implement, run, and inspect a simple program yourself</li>

 <li>So am I an assembly language programmer yet??</li>

</ol>

<strong><em><u>NOTICES</u></em></strong>​<strong><em>:  </em></strong>

<ol>

 <li><strong><em>We do encourage you to help one another and actively collaborate on your </em></strong><u>​<strong><em>lab exercises</em></strong></u><strong><em>  </em></strong><strong><em>(but NOT on your programming assignments, not EVER!)</em></strong></li>

</ol>

<strong><em>If you have taken this class before, you are required to </em></strong>​<strong><em><u>delete</u></em></strong>​<strong><em> all lab exercises and programming assignment code from your previous attempt. </em></strong>

<strong><em>See also the </em></strong><a href="https://docs.google.com/document/d/1ZAP5-95wBIGKzUerYwobp6NjN_iw3_Yn7j2WeZewvxE/edit?usp=sharing">​</a><a href="https://docs.google.com/document/d/1ZAP5-95wBIGKzUerYwobp6NjN_iw3_Yn7j2WeZewvxE/edit?usp=sharing"><strong><em>class collaboration policy</em></strong></a><a href="https://docs.google.com/document/d/1ZAP5-95wBIGKzUerYwobp6NjN_iw3_Yn7j2WeZewvxE/edit?usp=sharing">​</a><strong><em>. </em></strong>

<ol start="2">

 <li><strong><em>You are required to have a laptop for use in this class. </em></strong></li>

</ol>

<em>You will be using the machines provided in lab, but you will use your laptops for assignments &amp; homework. </em>

<em>See the </em><a href="http://student.engr.ucr.edu/laptop.html">​</a><a href="http://student.engr.ucr.edu/laptop.html"><strong><em>BCOE laptop policy</em></strong></a><a href="http://student.engr.ucr.edu/laptop.html">​</a><em> for minimum laptop requirements. </em>

<strong><em> </em></strong>

<ol start="3">

 <li><strong><em>Read “</em></strong><a href="https://docs.google.com/document/d/1o9fxCjbIa9NWhcCpx7ZTmBN4CxomF7yMiY1_M0SfrcU/edit?usp=sharing">​</a><a href="https://docs.google.com/document/d/1o9fxCjbIa9NWhcCpx7ZTmBN4CxomF7yMiY1_M0SfrcU/edit?usp=sharing"><strong><em>Intro to Assembly Language</em></strong></a><a href="https://docs.google.com/document/d/1o9fxCjbIa9NWhcCpx7ZTmBN4CxomF7yMiY1_M0SfrcU/edit?usp=sharing">​</a><a href="https://docs.google.com/document/d/1o9fxCjbIa9NWhcCpx7ZTmBN4CxomF7yMiY1_M0SfrcU/edit?usp=sharing"><strong><em>“</em></strong></a>​<em> (review of lecture material). You </em><u>​<em>MUST</em></u>​<em> read this </em>​<em><u>BEFORE</u></em><u>​</u><em> lab </em></li>

</ol>

<h2>3.0    Getting set up</h2>

First, you need to set up remote access to your ​<u>cs account</u>​ from both your laptop and from the machine you will be working on in lab (the procedure is basically the same for both).

<u>LAPTOP:</u>​ ​You will use ​<a href="https://wiki.x2go.org/doku.php"><strong>X2Go</strong></a>​, a package which provides remote connection to a server.

Download the appropriate X2Go client for your OS, following the instructions ​<a href="https://sites.google.com/a/ucr.edu/cse-instructional-support/home/accounts?pli=1#x2go_client">here</a><u>​</u> ​<em>(you must be logged into </em><a href="http://rmail.ucr.edu/">​</a><a href="http://rmail.ucr.edu/"><em>R’Mail</em></a><a href="http://rmail.ucr.edu/">​</a><em> to access this site).</em>

<u>LAB MACHINE:</u>​ The X2Go client is already installed on the lab machines: locate the app icon in Applications-&gt; Internet, and drag it onto your desktop.

In both cases, open the X2Go app, select Session-&gt;New Session.

In the New Session window, set:

<u>Session name​</u>: to whatever you want ​<em>(e.g. “bolt”, or your name) </em>

<u>Host</u>​: ​<strong>bolt.cs.ucr.edu </strong>

<u>Login​</u>: your ​<strong>NetID</strong>​ ​<em>(i.e. your username, the name part of your @ucr.edu email address) </em><u>Session type​</u>: select ​<strong>XFCE</strong>​ from the drop-down list Leave default values for all other settings.

When you click OK, this will create a session icon.

Click this icon to launch the connection: you will be asked to provide your cs account password. <em>(Unfortunately, on the lab machines, you will have to recreate the session icon every time you log in; on your laptop it will be permanent). </em>




Now ​<a href="https://docs.google.com/document/d/1NmG-fl10JuaP6eanTY0beHdLxHO3ewfLYm-KPb6OLz8/edit?usp=sharing"><strong>set up your cs061 directories</strong></a>​ &amp; get them ready for your labs &amp; assignment.

<strong> </strong>

<h2>3.1    Basic skeleton for LC-3 programs</h2>

<strong> </strong>

Similar to C++, every LC-3 program has a certain amount of overhead necessary for making everything work properly. In <strong>C++</strong>​          , you might have something like the following:​

//

// File: main.cpp

// Description: A simple hello world-esque program

// Author: Noobie Q. Programmer // Date created: 1/1/2019

// Date last modified: 1/1/2019

//

#include &lt;iostream&gt;  using namespace std;




int main()

{ cout &lt;&lt; “Egads, this is the most fun I’ve had in years!” &lt;&lt; endl;  }




This source code is passed to a ​<em><u>compiler</u></em>​, which ultimately produces a machine language <u>​<em>executable</em></u>​.







In LC3, a basic program will have the following look:

;

; Author: Noobie Q. Programmer

; UCR NetID/CS username: nprog001

; Lab Section: xxx

; TA: Sean Foley

; Lab 1

; Date created: 1/1/2019

;




.orig x3000                  ; **ALL** your programs will start at x3000

; Instructions (i.e. LC-3 code)

HALT                        ; end of program code

<table width="534">

 <tbody>

  <tr>

   <td width="204">; Local Data </td>

   <td width="330">; pseudo-ops for hard-coding data go here</td>

  </tr>

  <tr>

   <td width="204">.end</td>

   <td width="330">; .end is like the “}” after main() in C++.; It means “no more code or data”</td>

  </tr>

 </tbody>

</table>




If you haven’t figured it out by now, LC-3 comments are denoted with semi-colons. They can be on a line by themselves or on the same line as actual code (at the end of the line).

This source code is passed to an <em><u>assembler</u></em><u>​   </u>​ – a much simpler beast than a compiler, but like a compiler it produces a machine language executable.

Pseudo-ops <em>(</em>​ <em>the keywords that start with a </em>​’.’​<em> – see next section for more details)</em>​ are like compiler directives, in that they tell the assembler how to set things up.

<strong> </strong>3.2    Introduction to the basics of LC-3 programming

An LC-3 program consists of three basic elements: pseudo-ops​ , ​ instructions​ , and ​ labels​   .​

<u>Labels</u> <u>​ </u>are simply “aliases” for memory addresses. These are really, really useful because they relieve​    the programmer of the responsibility of figuring out which line of code is at which memory address, allowing us to use symbolic names to point to data and instructions.

<u>Pseudo-ops</u> tell the assembler how to set things up before starting to translate the source code into<u>​       </u> machine language. They are a bit like compiler directives in C++, such as #include​             ​.

For example, the pseudo-op .FILL​       tells the assembler to write a hard-coded value into memory (i.e.​  RAM, or system memory). For example, the two .FILL pseudo-ops in Table 1 would write the value 6 into memory at x3005 <em>(</em>​ <em>aka DEC6)</em>​, and the value 12 into memory at x3006 <em>(</em>​ <em>aka DEC12)</em>​ before the program begins execution.

Note that you just need to label the lines – you don’t need to know the actual memory addresses corresponding to those labels – that’s the assembler’s job.

<h1><u>Table 1: Labels and Pseudo-ops</u></h1>

<table width="463">

 <tbody>

  <tr>

   <td width="192"><u>Memory address </u>x3005</td>

   <td width="66"><u>Label</u>DEC6</td>

   <td width="205"><u>Pseudo-Op​</u>    <u>​Hard-coded value</u>.FILL       #6</td>

  </tr>

  <tr>

   <td width="192">x3006</td>

   <td width="66">DEC12</td>

   <td width="205">.FILL       #12</td>

  </tr>

 </tbody>

</table>

<em>(The ‘#’ before the numbers means decimal, i.e base 10; ‘x’ means hexadecimal, i.e. base 16)</em>​.

Now we can refer to these memory locations (and therefore access the data stored there) using the names DEC6 and DEC12.

We will learn about another psudo-op ​.STRINGZ​ in a moment (in section 3.3).




<u>Instructions:</u>​  ​There are 15 LC-3 instructions, in three distinct categories:

<ul>

 <li>Arithmetic / Logic operations (addition, bitwise AND, etc)</li>

 <li>Data movement (moving data back &amp; forth between RAM and local registers)</li>

 <li>Program control (changing the order of execution of code – if statements, for loops, etc)</li>

</ul>




<strong>The following section illustrates one or two instructions from each of these categories.  </strong>

<u>3.2.1     Arithmetic / Logic Operations</u>

These instructions are used for manipulating values and doing calculations – Adding two numbers, bitwise AND’ing two words together, or taking the bitwise logical NOT of a word.

The LC-3 has 8 general purpose, 16-bit ​local registers​ (analogous to variables in C++), named R0 through R7, that can be used as temporary storage for performing such operations.

The ​ADD ​instruction (2’s complement integer data type)

This instruction adds two numbers, and writes the result to a register. It comes in two flavors: One in which both operands come from local registers; the other in which the first operand comes from a register, while the second is actually embedded in the instruction itself (“immediate” mode). See the <u>​</u><a href="https://drive.google.com/drive/folders/0B9AugYlANDZkdkJmUEw1VWFkazQ?usp=sharing">ADD tutorial</a><u>​</u> ​<em>(also on the Piazza Resources page,  “LC3 instruction set”)</em>​ for more details

<u>3.2.2     Data movement</u>

Data movement instructions are used when you want to copy a value from a memory location into a local register (“loading”), or copy a value from a register to a memory location (“storing”).  You will be doing this a ​<strong><em><u>lot</u></em></strong>​, since the LC3 can operate only on values in registers, not in memory.

The ​LD ​instruction (“Load Direct” – probably the most frequently used instruction!)

This instruction copies the contents of a specified memory location (identified by a label) into a register. See the ​<a href="https://drive.google.com/drive/folders/0B9AugYlANDZkdkJmUEw1VWFkazQ?usp=sharing">LD tutorial</a>

The ​LEA ​instruction (“Load Effective Address”)

This instruction translates a ​<em><u>label</u></em>​ – the name you give to a memory location – back into the 16-bit <em><u>memory address</u></em><u>​</u> it stands for, and stores that <u>​<em>address</em></u><u>​</u> into the specified register. <u>There is no actual data movement here​</u> – just the decoding of a label.  See the <u>​</u><a href="https://drive.google.com/drive/folders/0B9AugYlANDZkdkJmUEw1VWFkazQ?usp=sharing">LEA tutorial</a>

<u>3.2.3     Program control</u>

These instructions are used in control structures such as BRANCHING​        , ​ LOOPING​      , and ​ SUBROUTINE​   CALLS ​<em>(a simpler version of function calls in higher-level languages)</em>​.

By default, a program starts at the first instruction and executes one instruction after another in order until it reaches the end (“sequential execution”).

Control instructions allow us to alter the default sequencing in several ways.

The ​BR ​instruction (“Conditional Branch”) can be used to transfer control to the instruction at a specified label based on a ​<em>condition</em>​.

<strong><em><u>All</u></em></strong><u>​</u> the control structures you are familiar with from C++ (if; if-else; if-else if-else; for; while; do-while; switch) can be built using this instruction, often in combination with the ​JMP​ instruction.




But before we can learn how it works, we have to know about the <u>​</u><a href="https://docs.google.com/document/d/1o9fxCjbIa9NWhcCpx7ZTmBN4CxomF7yMiY1_M0SfrcU/edit#bookmark=id.xve3xutg9b3g">Condition Codes</a><u>​</u><a href="https://docs.google.com/document/d/1o9fxCjbIa9NWhcCpx7ZTmBN4CxomF7yMiY1_M0SfrcU/edit#bookmark=id.xve3xutg9b3g">:</a>

Three “flags” (single-bit registers) are set whenever a value is written into any one of the local registers, and indicate whether the value being written is Negative, Zero, or Positive. These flags are called the

​N Z P Condition Codes​, and allow us to make decisions based on the last value written to a register – referred to as the last modified register (“<u>​<strong>LMR”</strong></u>​).




The decisions are actually made by the conditional branch instruction BR, which has three possible modifiers: {​n, z, p​}.

As you can guess, the n modifier asks whether the N Condition Code is currently set or not ​<em>(was the value just written negative?)</em>​; and likewise for the z and p modifiers.

The BR instruction can be modified by any combination of n, z, p. It will cause a branch to the labelled instruction ​<strong><em>IF AND ONLY IF</em></strong>​ any one of the specified conditions is met.  See the <u>​</u><a href="https://drive.google.com/drive/folders/0B9AugYlANDZkdkJmUEw1VWFkazQ?usp=sharing">BR tutorial</a>







<strong>3.3    </strong>​<strong><u>Exercise 0: lab01_ex0</u></strong><u>​</u><em> (aaargh!! not “hello world” again?!?!) </em>

<em> </em>

As always, the very first program we will write will simply output the message “Hello World!”  Though simple, it will illustrate several of the points above, plus some things you will fully understand only later on ​<em>(exactly like when you first encountered </em>​cout<em> in C++)</em>​              ​:

<ul>

 <li>We will store the string as an array of ASCII characters in memory, starting at an address labelled “message”, using the pseudo-op ​.STRINGZ</li>

</ul>

This pseudo-op stores a string in memory, one character per memory address, with a zero (“the null character” or ‘ ’) after the last character.

You will recognize this as a “c-string”, i.e. a null-terminated character array. So the line:

shrug.STRINGZ “whatever”  will write the characters  ‘w’  ‘h’  ‘a’  ‘t’  ‘e’  ‘v’  ‘e’  ‘r’  followed by x0000, to the nine memory locations starting with the labelled address shrug.

<ul>

 <li>We will use the LEA instruction to translate the label “shrug” into its actual address, which we will store in R0.</li>

 <li>We will invoke an i/o subroutine called PUTS ​<em>(can also be written as </em>​TRAP x22<em>)</em>​​, which uses R0 to locate the string ​<em>(it knows when to stop because the last value in the char array is ‘ ’)</em>​.</li>

</ul>

Now write this program for yourself:




<ol>

 <li>In your terminal, navigate to ​cs061/labs/lab1​, and open your exercise 0 file in geany: <strong>geany lab01_ex0.asm &amp; </strong></li>

 <li>Copy in the code from the above image &amp; save the file <em>(</em>​ <em>you can leave the editor open if you wish)</em>​.</li>

 <li>From your terminal, launch the LC-3 assembler/emulator: <strong>simpl lab01_ex0.asm &amp;</strong></li>

</ol>

This will open two windows:

<ol>

 <li>the ​emulator​ itself, showing the state of the processor, including the registers, the condition codes, the assembled code (“machine language” or “binary”) in memory; and</li>

 <li>the ​console​, where all output from the program is displayed, and where you can type input to the program. ​<em>(You may have to move the emulator to find the console!) </em></li>

</ol>

<ol start="4">

 <li>Now you will open a third, the ​Text Window​. This can be used to enter command line input to the emulator, but we will use it mostly to watch for warnings and error messages. <strong>Check the Text Window box</strong>​ at the bottom center of the emulator window.</li>

 <li>Hit the ​<strong>Run</strong>​ button at the bottom of the emulator window (or enter the word “run” in the Text Window input box), and observe the words “Hello World!” magically appear in the console window!</li>

</ol>




<h2>3.4     Exercise 1:  lab01_ex1 – A “real” program</h2>

<strong> </strong>

Now Hello World is out of the way, we can write a program that actually does some processing: it will multiply a number, which we will store in advance in memory, by six ​<em>(How hard can that be, right??!?) </em>




We will also take this opportunity to introduce the style you <u>​<strong><em>MUST</em></strong></u>​ use for all your LC-3 programs.




See the image below:




First comes the header, which will always be included in your starter code: obviously, you have to always fill it out with your personal details.




Next, we have the line ​.orig x3000

This indicates where in memory the code will reside. The LC3 assembler requires all programs to be loaded at or above x3000: all your programs ​<strong><em><u>must</u></em></strong>​ load the “main” routine to x3000  <em>(just try something else and see what happens!! On second thoughts – don’t!) </em>




The code itself multiplies 6 by 12: but since the LC-3 has no multiply instruction ​<em>(really!!)</em>​, the operation has to be carried out by adding 12 into an accumulator 6 times.

<em>We could have added 6 into an accumulator 12 times: why would that not be a good idea? </em>




<em>Can you see how this program works? </em>




The next three lines load hard-coded values from memory into registers R1, R2, and R3 respectively:

R1 is an “accumulator” – i.e. at the end, it will hold the result – so we have to initialize it to 0;  R2 holds the number to be multiplied; and

R3 is used as a loop counter (to keep track of how many times the loop will execute – i.e. a “counter-controlled” loop).

<strong><em>Make sure you understand how the BRp instruction controls the loop – this is the foundation of all Assembly Language control structures!! </em></strong>




<strong><u>TIP:</u></strong> Actually, copying values from memory to register (and vice versa) is rather inefficient.​     Mostly, we can’t avoid it – our fixed data has to be stored in memory.

However, there is one special value for which we can do better – 0!

There is a much cleaner way to “zero out” a register than copying a hard coded 0 from memory to register:

<strong>AND R1, R1, x0    ; R1 &lt;- (R1) AND x0000 </strong>

This does what we call a “bitwise AND” of R1 with 0, i.e. it ANDs each of the 16 bits in R1 with 0, and stores the result (0) back in R1 – a LOT quicker than reading from memory!




Note how the program data is stored in a block separated from the code, <strong><em>following</em></strong>​          ​ the HALT instruction, which ends code execution.




And finally, note how we use comments to “partition” the file into instructions and data.

Now that you have had a nice lengthy overview of some basic LC-3 instructions and seen how to use the simpl assembler/emulator, it is time for you to implement the program yourself.




Open file <strong>lab01_ex1.asm</strong>​        for editing, type in the code from the image, save it, and open it in simpl.​ <em>Remember to replace the first LD R1 instruction with the AND instruction. </em>

<strong> </strong>

This time, instead of hitting Run, step through each line of code using the <strong>Step </strong>​    button in the emulator​ until you reach the HALT instruction. Notice how the value of R1 keeps going up by 12 until it reaches <em>(guess what??)</em>​ 72

<em>(Now, how did it know to stop at just the right number??) </em>




Finally, congratulate youself on a job well done &#x1f642;



<div align="center">

## How windows works \(part 1\)


</div>

### Description

A beginners guide to how windows (tm) works
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Duncan Jones](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/duncan-jones.md)
**Level**          |Beginner
**User Rating**    |4.8 (24 globes from 5 users)
**Compatibility**  |VB 4\.0 \(32\-bit\), VB 5\.0, VB 6\.0, VB Script, VBA MS Access, VBA MS Excel
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__1-1.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/duncan-jones-how-windows-works-part-1__1-34101/archive/master.zip)





### Source Code

<p><b><i>How we got to where we are now</i></b></p>
<p><b>Command line programs</b></p>
<p>
In the beginning was the command line program. This took input from the keyboard (usually in the form of parameters ) and printed text output on a screen or printer. The program flow starts, picks up any parameters, outputs the results and terminates.</p>
<p>
An example of this is the DIR command. When you type "DIR /ad [return]" at the command prompt the operating system starts the program called DIR and passes it the argument /ad. The DIR program takes this, produces an output (a directory listing of any subdirectories of the current directory), and then terminates.</p>
<p>
This was extremely fast and simple to program, but not overly powerful. You can't do a whole lot with parameter passing (though hardened UNIX programmers may disagree) and remembering the format and number of parameters was onerous.
</p>
<p>
Out of this need came the programs which could be interacted with. Such programs needed to take the input from the keyboard and modify their display accordingly. To do this they had a central loop of code, which went along the lines of "read the next key, process the key, if the key isn't exit then repeat". Since the processing of one key press might take a long time and it was bad form to prevent the user typing whilst processing was continuing, a queue of key presses was maintained where keys were added to one end by the user pressing the keyboard and removed off the other end by the program loop. </p>
<p>
Then, spurred on by the massive advances in hardware power, the users became plain greedy. No longer content to close down one program in which they were typing up a management report to open another which held the figures and then close that down to go back again, they decided that they wanted to switch between programs running at the same time . In order to do this, the running program had to watch out for the "switch" key, and save off it's current state (usually in dynamic memory) before transferring control to the next program in the running programs collection.</p>
<p>
<b>The graphical interface</b></p>
At about the same time (in human terms, as computing progress runs much faster), people at Xerorx PARC began changing the way the user interacted with their programs. What started as on screen indications of what else was running soon became a method whereby each running program had it's own little section of the visible screen which it could write to…and windows was born. Of course, this graphical interface was tricky to use with the keyboard alone, and the mouse was born just a cosmic blink later.</p>
<p>
<b><i>The "problems", and how Windows ™ solves them</i></b></p>
<p>
<b>1 How does it know which program I am typing in?</b></p>
<p>
Every program (also known as an application) has a main window. This is usually (though not always) the one with the name of the application in its title bar. For instance, I am typing this in Microsoft Word™, and the title bar says "Microsoft Word - Document 1". Now, whilst there are a number of programs all with their main windows open, only one program has the "focus" at any given time. </p>
<p>
<b>Focus?</b> This means that the key presses are being sent to a queue which is only for that parent window, and each window has to maintain its own queue. Focus can be switched between windows by Alt-Tabbing from one to another or by activating an application by clicking the mouse on it.</p>
<p>
<b>2 When I move one window over another, how does the latter know to repaint itself.</b></p>
<p>
To be brief, what happens is that a message is sent by the operating system to each of the visible windows telling it which region needs painting, and they respond by repainting that part of their window. Sometimes when a program is very busy or quite badly written, it doesn't have time to update itself which is why dragging one window over another may appear to erase the one underneath.
</p>
<p>
Messages are a fundamental part of Windows™. Everything the user does (clicking the mouse, pressing a key etc) causes a message to be sent to a window. As with the early interactive programs, each window has a queue. Unlike the early programs, these queues can hold a large number of different types of message e.g. the user clicked here, this program asked me to repaint myself, the user has changed the date format etc. The program can process the message, pass it on to another window, fire off it's own messages in response or even ignore it altogether. All this is done by a code loop which has evolved from that involved in in the earliest interactive programs.</p><p>
<b>3 There must be hundreds of messages - how does every program know what to do with them?</b></p>
<p>
There are indeed hundreds of different message types, and more are being added all the time. Fortunately, if (as a programmer) you want to handle a message in a standard way you don't have to write any code so to do. You simply pass the message on to the "Default Window Process" which deals with it for you. A glance at my "windows messages" reference manual, all 1200 pages, shows why this is a very good thing.</p>
<p>
<b>4 There are loads of different windows, all loaded at the same time. How does Windows™ know which is which?</b></p>
<p>
When a new window first is created, it gets given a unique number. This is generally known as the window handle. This handle is to tell windows where a message is meant to go, where the code which processes the windows messages is etc.
</p>


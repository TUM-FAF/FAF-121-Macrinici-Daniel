Windows Programming Laboratory Work #1
======================================

Title
-----
Window. Window handling. Basic window’s form elements.

Introduction
------------
Main purposes of this lab work:
* Understand Event-Driven Programming.
* Study Win32 API.

Secondary purposes of this lab work:
* Use a Version Control Systems (GIT).
* Write code according to a Programming Style Guide.

Mandatory Objectives
--------------------
* Create a Windows application
* Choose Programming Style Guidelines that you'll follow
* Add 2 buttons to window: one with default styles, one with custom styles (size, background, text color, font family, font size)
* Add 2 text inputs to window: one with default styles, one with custom styles (size, background, text color, font family, font size)
* Add 2 text elements to window: one with default styles, one with custom styles (size, background, text color, font family, font size)

Objectives With Points
----------------------
* Make elements to fit window on resize. **(1 pt)**
* Make elements to interact or change other elements. **(2 pt)**
* Change behavior of different window actions (at least 3). **(1 pt)**
* Write [your own PSG](https://github.com/TheRedGuy/Style-Guides/wiki/C-Style-Guide). **(1 pt)**

Programming Style Guide
-----------------------
For this laboratory work, I elaborated a [C Programming Style Guide](https://github.com/TheRedGuy/Style-Guides/wiki/C-Style-Guide), 
which was inspired by [Rhombus C style guide](https://github.com/nickbjohnson4224/rhombus/wiki/C-style-guide). 
I also added to this PSG a section specific for Windows Programming with Win32 API. 
I intend to continue using, and developing this PSG, because it insures code consistency, and readability.

Application Creation Steps
--------------------------
In the development process, I consulted the recommanded book (["Programming Windows, 5th Edition", by Charles Petzold](http://www.charlespetzold.com/pw5/)).
Also, I found myself consulting the documentation on the [MSDN](http://msdn.microsoft.com) page.

This simple windows application consists of two main parts: the WinMain Procedure and the WindowProcedure procedure (just WindowProcedure for further reference).
Following this logic, I created and declared the main window class along with its functionality and behavior within the context of WinMain. In addition to that,
I added all the window elements (such as buttons, text input fields, scrollbars) in the WindowProcedure. 

Processing the message loop, the WindowProcedure analyzes window messages and executes different actions based on some conditions and/or events.


Below, I present a wireframe model of the application general layout and functionality, using the [MockFlow](http://mockflow.com/) tool.

![Mockup](https://github.com/TUM-FAF/FAF-121-Macrinici-Daniel/blob/master/WP/Lab%231/pictures/Wireframe1.png)

The dialog bubbles describe each element and its functionality.

Result Application
------------------
This is a screenshot of the application in the Windows 7 environment:

![Screenshot](https://github.com/TUM-FAF/FAF-121-Macrinici-Daniel/blob/master/WP/Lab%231/pictures/Screenshot.PNG)

Conclusions
-----------
Although I don't intend to become a Windows developer, nor I use a Windows system in my development projects, I found this laboratory work very usefull, 
because I gained experience in Event-Driven Programming, which aided my understanding of this paradigm. 
I find the knowledge gained during this laboratory work to be very important, because these concepts can be applied not only in Windows Programming, but in developing any system which uses message-sending and Event-Driven Programming.

The Windows API is the source code interface that is used to create Windows applications. I found this laboratory work very useful, because I gained
experience in Event-Driven Programming, which aided my understanding of this paradigm. I find the knowledge gained during this laboratory work to be very
important, because these concepts can be applied not only in Windows Programming, but in developing any system which uses Message-Sending and Event-Driven Programming.

I am pleased that I have found a programmatic way to create a customized button, although I think the downside of this decision is the increase in the complexity
of the code, contrary to the KISS principle. So, a solution for this scenario would be implementing the customized buttons using resource files.
I can also improve the application by the usage of PostMessage( ) method instead of SendMessage( ) routine, because the latter awaits for the ending of the
message processed at the moment of execution, while there is no such need for this instance.
This laboratory work gave me a good insight, upon which to lay a sound foundation on Windows API.

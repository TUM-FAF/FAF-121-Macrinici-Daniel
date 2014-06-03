Windows Programming Laboratory Work #2
======================================


Title

-----

Advanced form elements. Child Windowses. Keyboard basics



Purpose
------------

Gain knowledge about basics of working with child window controls, such as Scrollbars and Listboxes. Learn how to create menus and other resources. Implementing dialog boxes (the easy way, through  a .rc file) and learning how to hook events to the keyboard.


Mandatory Objectives

--------------------

* Display a dialog box on some event (ex. on clicking some button)
* Add a system menu to your application with at least 3 items (add actions to that items)* Add 2 text elements to window: one with default styles, one with custom styles (size, background, text color, font family, font size)
* Add a scroll bar that will change any visible parameter of any other element (color of a text)
* Hook keyboard input. Add 2 custom events for 2 different keyboard combinations (ex. change window background on ctrl+space) 



Objectives With Points

----------------------

* Add a listbox and attach some events when any element is accessed (clicked)** (2 pt) **

* Add 2 scroll bars that will manage main window size or position **(1 pt)** 
* Customize your application by adding an icon and using different cursor in application **(1 pt)** 

* Use a scroll bar to scroll through application working space. Scroll should appear only when necessary (eg. when window width is smaller than 300px) **(1 pt)** 


Application Creation Steps
-----------------------


In the development process, I consulted the recommended book ("Programming Windows, 5th Edition", by Charles Petzold). Also, I found myself consulting the documentation on the MSDN page.
For developing the project, I've used the CodeBlocks IDE. The project can be simply compiled having the ** .cbp * file and the resource ** .cpp *. 
I organized this laboratory work into three files (main.cpp, resource.h and menu.rc). The last two files store the numerous identifiers to the control handles in the application and also the description of the menu and custom icon.
The most difficult part was working with scrollbars. When implementing them, two essential functions must be provided:

BOOL SetScrollRange(
  _In_  HWND hWnd,
  _In_  int nBar,
  _In_  int nMinPos,
  _In_  int nMaxPos,
  _In_  BOOL bRedraw
);

, where hWnd is the handle to a scrollbar control or a window with a standard scroll bar, depending on the value of the nBar parameter; nBar [in] Specifies the scroll bar to be set. This parameter can be one of the following values: SB_CTL, SB_HORZ,  SB_VERT. In our case SB_CTL is used because my program emphasizes the work with scrollbar controls, which provides extra functionality.

int SetScrollPos(
  _In_  HWND hWnd,
  _In_  int nBar,
  _In_  int nPos,
  _In_  BOOL bRedraw
);

Here the parameters are essentially the same, except of the last one, which is a bool value that Specifies whether the scroll bar is redrawn to reflect the new scroll box position. If this parameter is TRUE, the scroll bar is redrawn. If it is FALSE, the scroll bar is not redrawn.
Moreover, when working with scrollbar controls, I had to analyze two cases, namely the case WM_VSCROLL and case WM_HSCROLL messages, in which the behavior of the window (elements) is described.
What I also found interesting was implementing the keyboard events, which in my case were the ctrl+space and ctrl+f1 button events. The events processing was comprised in the WM_KEYDOWN message, by varying the wParam parameter and separately analyzing the cases (case VK_SPACE and  case VK_F1).

Regarding the child window controls, an essential function which provided communication is the SendMessage function, which sends the specified message to a window or windows. The SendMessage function calls the window procedure for the specified window and does not return until the window procedure has processed the message.

LRESULT WINAPI SendMessage(
  _In_  HWND hWnd,
  _In_  UINT Msg,
  _In_  WPARAM wParam,
  _In_  LPARAM lParam
);

hWnd [in]- A handle to the window whose window procedure will receive the message.
Msg [in]- The message to be sent.
wParam [in]- Additional message-specific information.
lParam [in]- Additional message-specific information.






Conclusions

-----------



I found this laboratory work very useful, because I gained insights of the concepts of child window controls, the relationship between them and the Main Window Procedure and also the additional effects that the user can enhance the program with, through custom descriptions in the resource files. The first attempt to create an UI, was rather decent, but still great, the thing which offered me a better explanation of how complex programs work.
Windows Programming Laboratory Work #3
======================================


Title

-----

Windows Timer. Animation.



Purpose
------------

Gain knowledge about basics of working with **Windows timer**


Mandatory Objectives

--------------------

* Create an animation based on Windows timer which involves at least 5 different drawn objects


Objectives With Points

----------------------

* Increase and decrease animation speed using mouse wheel (2 pt) 
* Solve flicking problem (2 pt) please describe in your readme/report how you did it 
* Add animated objects which interact with each other (2-6 pt), ex.: 
* Few balls which have different velocity and moving angles. In order to get max points, add balls with mouse, make balls to change color on interaction and any other things that will show your engineering spirit	*Any other interesting and reach in animation application
* Animate a Nyan Cat that leaves a rainbow tail (Math.floor(+35% for task with interacting objects)) 


 
Application Creation Steps
-----------------------

In the development process, I consulted the recommended book ("Programming Windows, 5th Edition", by Charles Petzold). Also, I found myself consulting the documentation on the MSDN page.
For developing the project, I've used the CodeBlocks IDE. The project can be simply compiled having the ** .cbp * file and the resource ** .cpp *. 
The flickering problem occurs when an image is displayed on top of another in rapid succession.
A common method to completely eliminate flickering windows is to use a technique called double-buffering. This basic idea is to draw a window's contents into an off-screen buffer, and then transfer this buffer to the screen in one fell-swoop (using BitBlt).

The way I solved this problem is: 

case WM_PAINT:
 
    // Get DC for window
    hdc = BeginPaint(hwnd, &ps);
 
    // Create an off-screen DC for double-buffering
    hdcMem = CreateCompatibleDC(hdc);
    hbmMem = CreateCompatibleBitmap(hdc, win_width, win_height);
 
    hOld   = SelectObject(hdcMem, hbmMem);
 
    // Draw into hdcMem here
 
    // Transfer the off-screen DC to the screen
    BitBlt(hdc, 0, 0, win_width, win_height, hdcMem, 0, 0, SRCCOPY);
 
    // Free-up the off-screen DC
    SelectObject(hdcMem, hOld);
    DeleteObject(hbmMem);
    DeleteDC    (hdcMem);
 
    EndPaint(hwnd, &ps);

One more important thing regarding the memory:
Because I used doublebuffering, more memory is used. Which is why, I imposed a limit for the drawn objects in the program to be 30. So in order to prevent overflow, the following code eliberates the memory and then allocates it back for the objects:

<code> if (NrRings == 30)
            {
                delete [] B;
                Ring* B = new Ring[30];
                NrRings = 0;
            }
</code>

For drawing the objects themselves, Arc function was used, which draws an elliptical arc.

<code>
		BOOL Arc(
		  _In_  HDC hdc,
		  _In_  int nLeftRect,
		  _In_  int nTopRect,
		  _In_  int nRightRect,
		  _In_  int nBottomRect,
		  _In_  int nXStartArc,
		  _In_  int nYStartArc,
		  _In_  int nXEndArc,
		  _In_  int nYEndArc
		);
</code>

, where the first parameter is a handle to the device context where drawing takes place; the following four parameters are describing the upper left coordinate pair of the arc to be drawn and respectively the lower right corner;  and the last four are describing the coordinates of the ending point of the radial line defining the starting and ending point of the arc.



Conclusions

-----------

I found this laboratory work very useful, because I gained insights of the concepts of windows timer, and how to build animation using the timer (using srand and rand functions in help). The first attempt to create an animation application, was rather difficult, namely because the dynamics and mechanics of interaction between object is not so easy to implement, but it was still rewarding. The program needs to be improved to behave properly when the user maximizes and minimizes the window (currently these functions are programmatically disabled).


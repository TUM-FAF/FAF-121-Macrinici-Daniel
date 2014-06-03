Windows Programming Laboratory Work #3
======================================


Title

-----

Basics of Working with Mouse. GDI Primitives. Bezier Curve.



Purpose
------------

Gain knowledge about basics of working with mouse, device context and also GDI Primitives, such as Lines, Curves, Planes, Bitmap Images, and in addition construct a Bezier Curve.


Mandatory Objectives

--------------------

* Draw few lines of different colors and weights
* Draw a Bezier curve
* Draw few plane objects (ex. circle, square, pie, polygon...) of different colors, weights, filled and not
* Draw 2 different objects using mouse


Objectives With Points

----------------------

* Draw a custom bitmap image (1 pt) 
* Add a switch (button, select list...) that will change mouse ability to draw objects (2 pt) 
* Draw a Bezier curve using mouse (1 pt) 
* Fill an object with a gradient (1 pt) 
* Delete objects using mouse clicking (2 pt) 
* Use mouse as an eraser of: 
* a fixed width (1 pt) 
* a adjustable width (2 pt) 
* Zoom in and out application working area using keyboard (2 pt) 

 
Application Creation Steps
-----------------------

In the development process, I consulted the recommended book ("Programming Windows, 5th Edition", by Charles Petzold). Also, I found myself consulting the documentation on the MSDN page.
For developing the project, I've used the CodeBlocks IDE. The project can be simply compiled having the ** .cbp * file and the resource ** .cpp *. 
Because this lab represents the basics of work with GDI, I have used many built-in GDI functions, such as LineTo, Ellipse, Rectangle, PolyBezier, which were residing in my implemented custom functions , which all contained the POINT structure array, which defines the x- and y- coordinates of a point. 

typedef struct tagPOINT {
  LONG x;
  LONG y;
} POINT, *PPOINT;

Moreover, I had learned how to use checkboxes, radiobuttons and comboboxes. They are not difficult to grasp, but nevertheless the syntax may seem a little messy when implementing, for instance, comboboxes. As an example of that, here I provide a code snippet:

SendMessage(hCmbxThickness,
                        CB_ADDSTRING,
                        0,
                        reinterpret_cast<LPARAM>((LPCTSTR)"1"));
						
,where hCmbxThickness is the handle to the window containing the combobox; CB_ADDSTRING - Adds a string to the list box of a combo box; and reinterpret_cast<LPARAM>((LPCTSTR)"1") – which is an additional message-specific information with the purpose of specifying the first field in the combobox.
The work with the mouse resides mainly within the WM_LBUTTONDOWN, WM_LBUTTONUP, WM_MOUSEMOVE messages, which in my opinion was the most difficult part of this laboratory work. One example of this lays in the WM_LBUTTONDOWN message, where the programmer must analyze all possible cases of the behavior of the program when the user holds down (clicks) the left button (when drawing a figure: Line, Circle, Rectangle, Bezier Curve; when using the eraser;). The most interesting work with the geometry was obviously with Bezier Curves implementation, because in comparison to the other simpler figures, it requires four points ( endpoint and control points specified by the lppt parameter:

BOOL PolyBezier(
  _In_  HDC hdc,
  _In_  const POINT *lppt,
  _In_  DWORD cPoints
);

In which, hdc[in]- A handle to a device context; lppt [in]- A pointer to an array of POINT structures that contain the endpoints and control points of the curve(s), in logical units; cPoints [in]- The number of points in the lppt array. This value must be one more than three times the number of curves to be drawn, because each Bezier curve requires two control points and an endpoint, and the initial curve requires an additional starting point.
One core function that was used in the program was SelectObject function, which requires a handle to the device context and  a handle to the object to be selected, in my case to the Pens and Brushes I’ve declared using the functions setupPen and setupBrush.


Conclusions

-----------

I found this laboratory work very useful, because I gained insights of the concepts of Graphical Device Interface primitives, working with the mouse (handling mouse messages, separating cases),  and also the implementation of the geometry behind the drawn figures. The first attempt to create an application which resembles Microsoft PAINT, wasn’t very efficient, because of some bugs in the program related to the invalidation of the working region of the screen(in the way that if a figure is drawn above other figures, the latter disappear). But it was still great and fun to work with.


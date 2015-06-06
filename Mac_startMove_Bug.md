Multi-screen Drag works perfect in Windows but has strange bug in Mac OS X.

Restoring, resizing or moving a NativeWindow and trigger a startMove() within 5 animation frames and 1 mouse click will cause the window fly far far away from it's previous position.

Solution A

If startMove() is delayed for 5 frames, which is a practical value I found on my Mac Book, it's yet not perfect. If you don't move your mouse during the 5 frames, startMove() will cause the NativeWindow to align its origin (0,0) right to your mouse position, instead of start moving right from the current place.

Solution B

To separate restore / resize / reposition from startMove() seems the safest and flawless way, though you need 2 clicks to achieve a Multi-screen Drag. First click the Move button on the dragger (title bar) to show the Drag Panel and release your mouse. Then drag the panel to roll out and release to hide the panel.
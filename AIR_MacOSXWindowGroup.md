How to move the a NativeWindow above the Mac OS X menu bar, right on the top of the screen?

# Introduction #

In Mac OS X, mine is 10.5 Leopard, when you drag a window, its title bar is usually restrained below the system menu bar. For Normal Mode Pixus under Mac OS X, when you drag the frame upward, you will see it ends up about 100px below the menu bar. That's because the invisible NativeWindow is restrained. Windows doesn't have such a limitation.

# Details #

I have found an article on Apple Mailing List. It described that by using a higher level Window Group than the system menu bar's, the window can move off the top of the screen. But it's a part of the Carbon API. I don't see anything within NativeWindow class can handle it. Any one can give me some direction? Below is the article.

```
Actually, I forgot about one special case. The Window Manager will not restrict the window's movement if the window level of the window is greater than the window level of the menubar. So you should be able to do this by creating a new window group, setting the window group's level to a value one greater than the menubar, and putting your window into that group. Something like this:

WindowGroupRef aboveMBarGroup;
CreateWindowGroup( 0, &aboveMBarGroup );
SetWindowGroupLevel( aboveMBarGroup, kCGMainMenuWindowLevel + 1 );
SetWindowGroup( aboveMBarWindow, aboveMBarGroup );

This will work in 10.1 and later.

-eric
```
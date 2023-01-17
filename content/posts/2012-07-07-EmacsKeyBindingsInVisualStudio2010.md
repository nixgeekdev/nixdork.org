---
title: 'How to use Emacs key bindings in Visual Studio 2010'
slug: 'how-to-use-emacs-key-bindings-in-visual-studio-2010'
date: 2012-07-07T20:33:04-08:00
tags: ['programming', 'csharp', 'emacs']
---

Visual Studio 2008 used to have a Emacs key mapping scheme that you could pick
from the Options dialog under the Keyboard options. Visual Studio 2010 did away
with that key mapping scheme.

![VS2010 Keyboard Mapping Schemes](http://farm9.staticflickr.com/8167/7524332504_88780c5245.jpg)

But those emacs enthusiasts among us who use Visual Studio should not
fear... There is now an Emacs Emulation extension available for VS2010 that you
can install via the Extensions Manager under the Tools menu.

## Installation

To install the Emacs Emulation extension, follow these steps:

![VS2010 Extensions Manager](http://farm9.staticflickr.com/8023/7524332642_147e3ebc33.jpg)

1. Open Visual Studio 2010
2. Go to the Tools menu
3. Select the Extension Manager
4. On the Extension Manager dialog, select Online Gallery
5. Search the Online Gallery for Emacs (top right)
6. Select and install the Emacs Emulation package
7. Restart Visual Studio 2010
8. From the Options dialog, the Emacs key mapping scheme is now available

![VS2010 Emacs Keyboard Mapping Scheme](http://farm8.staticflickr.com/7130/7524332716_e2e039ab36.jpg)

Beyond the default Emacs key bindings, the ones that I find most useful are the
following:

    Edit.EmacsExtendedCommand
    :   *ALT + X* - Places the cursor in the Find/Command box on the Standard toolbar.

    Edit.EmacsFindReplace
    :   *SHIFT + ALT + 5* - Displays the replace options in the Quick tab of the Find and Replace dialog box.

    Edit.EmacsSwapPointAndMark
    :   *CTRL + X, CTRL + X* - Moves the cursor to the current mark in the location stack and moves the current mark to the location where the cursor mark was when the command was invoked.

    Edit.EmacsCloseOtherWindow
    :   *CTRL + X, 1* - When a window is split, this shortcut closes the pane that does not have focus.

    Edit.EmacsSplitVertical
    :   *CTRL + X, 2* - Splits the current document in half vertically. The current line of code is centered in each window.


... and that's all, folks!

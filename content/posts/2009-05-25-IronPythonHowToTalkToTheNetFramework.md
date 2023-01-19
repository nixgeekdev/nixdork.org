---
title: 'Iron Python: How to talk to the .NET Framework'
slug: 'iron-python-how-to-talk-to-the-net-framework'
date: 2009-05-25T22:00:00-08:00
tags: ['python', 'programming']
---

[Iron Python](http://www.codeplex.com/Wiki/View.aspx?ProjectName=IronPython) is
an implementation of the [Python](http://www.python.org/) programming language
that runs on the
[Common Language Runtime](http://en.wikipedia.org/wiki/Common_Language_Runtime)
and can use the classes of the
[.NET Framework](http://en.wikipedia.org/wiki/.NET_Framework).

Here are some quick notes on how to interface with the framework from Iron
Python:

1.  Open the Iron Python REPL.
2.  Import the `clr` module.
3.  Add a reference to the .NET Namespaces you want to interact with.
4.  Start using the .NET classes as if they were Python classes.

Below I transcribed a little code snippet for you to use as an example. I also
provide a screen capture of the sample and the outcome of running it.

     import clr
     clr.AddReference("System.Windows.Forms")
     from System.Windows.Forms import Application, Form, Button, MessageBox

     f = Form()
     b = Button()

     f.Text = "Hello World!"
     b.Text = "Click Me!"

     def clicked(sender, args):
         MessageBox.Show("Hello, Again...")

     b.Click += clicked
     f.Controls.Add(b)
     f.ShowDialog()


[![Iron Python][2]][1]

Enjoy!

[1]: http://www.flickr.com/photos/gorauskas/3565205389/ ""
[2]: http://farm4.static.flickr.com/3327/3565205389_ccd811cf67.jpg

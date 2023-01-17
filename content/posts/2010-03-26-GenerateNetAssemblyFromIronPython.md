---
title: 'Generate .NET Assemblies from Iron Python'
slug: 'generate-net-assemblies-from-iron-python'
date: 2010-03-26T06:32:00-08:00
tags: ['python', 'programming']
---

The other day I was talking to a fellow programmer and the question of compiling
Iron Python code into .NET assemblies came up. So what if you have an Iron
Python script that you want to run and then have the `ipy` interpreter output an
assembly that you can run on other machines. How do you do that?

There are several ways to approach the problem. One way is to use an IDE, but
IDE support for Iron Python is still a bit lacking. One IDE that provides Iron
Python great support is
[SharpDevelop](http://www.icsharpcode.net/opensource/sd/) create a Iron Python
project, write your code as you normally would and then build your project. The
compile assemblies can then be found in the build output folders for that
project.

The other way to do this is through a tool that ships with IronPython called Pyc
or the Python Command-Line Compiler. If you installed the latest version 2.6 of
IronPython, then `pyc.py` will be available at `C:\Program Files
(x86)\IronPython 2.6\Tools\Scripts` or wherever you installed IronPython
on your system. If you have earlier versions of IronPython then
`pyc.py` will be available as a separate download in the samples
package.

With `pyc.py` you can create console or Windows assemblies from your python
scripts. Basic usage looks like this:

    ipy pyc.py /out:myprogram.exe /main:mainfile.py /target:exe program.py support.py

The above will generate an assembly called `myprogram.exe` (`/out`) which is a
console application (`/target`) and will execute the code in `mainfile.py` first
(`/main`) and will also include code from `program.py` and `support.py` in the
assembly.

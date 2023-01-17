---
title: 'How to resize a VirtualBox VDI file'
slug: 'how-to-resize-a-virtualbox-vdi-file'
date: 2011-05-28T01:32:29-08:00
tags: ['bash', 'linux', 'virtualbox']
---

I am running Ubuntu Lucid on my workstation at home, but sometimes I still need
to go back to Windows to get something done that I haven't quite figured out
how to do in Linux yet. For that I am running VirtualBox on the workstation
from which I spin up a Windows 7 VM.

I initially created the VM with 32 GB of hard drive space. That turned out to
be too little and after the base Win7 OS and a few applications I was using
over 15 GB. So I figured that I needed more hard disk space and I thought that
I could just enlarge the pesky VDI file for the Win7 VM (it stands for Virtual
Desktop Image and that's the default VM image file format used by VBox).

[![Win7 VBox VM Before Resize][2]][1]

*Before*

Well, it turns out that *in nature* you can't really pick up a hard disk, open
it up, and throw in a new platter. In a *virtual* world, however, you get to
play *God* and manipulate it any way you choose. All you have to do is clone
and modify your original VDI file. Here's what you need:

1.  VirtualBox. [Read this](http://thestandardoutput.com/2011/05/virtualbox-on-debian-based-distros/,
    "Install VBox") to install it on a Debian-based Linux distro.
2.  Windows 7... But any other OS ISO image or disk will do.
3.  [GParted](http://gparted.sourceforge.net/, "GParted"), the Gnome partition
    editor.

Assuming that you already downloaded the GParted ISO, installed VirtualBox and
created some VM of which you want to resize the VDI file, here's how you do it:

1.  Open a terminal (we'll be using the command line for this).
2.  Find the VDI file you want to resize. This is usually under `~/VirtualBox VMs`
3.  Now clone the VDI by issuing the following command:

        VBoxManage clonevdi Win7_64bit.vdi Win7_64bit_Larger.vdi

    Where the first file name is the input file and the second file name the
    output.

4.  Then resize the VDI (I grew mine from 32 to 64 GB):

        VBoxManage modifyvdi Win7_64bit_Larger.vdi --resize 65536

    Where the first parameter is the input file name and the resize parameter
    takes the new size in megabytes.

5.  In the graphical VirtualBox manager, create a new VM using the cloned and
    expanded VDI file. I would pay special attention to use the same setting as
    the original VM that you cloned from.
6.  Now boot the new VM using the GParted ISO image that you downloaded
    earlier. We will use it to resize the partition inside the VDI.
7.  On the boot screen you will want to choose to boot using the Live GParted
    instance. We will use it to resize the partition in the VDI.
8.  Once the live CD has booted up and the GParted application is running,
    select the partition you want to resize by clicking on it and then click the
    resize button.

    [![GParted Step 1][4]][3]

9.  Then select the handle at the end of the partition and slide it to fill up
    the entire unused space area. Click the resize button.

    [![GParted Step 2][6]][5]

10. Next click the apply button on the GParted toolbar and watch the magic
    happen. Once done, click close and reboot the VM.

    [![GParted Step 3][8]][7]

11. The first time you boot after performing the steps above, Windows will
    likely want to check the disk for consistency. Let it happen and Windows
    will reboot itself.

[![Win7 VBox VM After Resize][10]][9]

*After*

After this process, my Windows 7 VM was able to see a much larger drive. Let me
know in the comments if you have questions or suggestions about how to improve
this process.


[1]: http://www.flickr.com/photos/gorauskas/5767015885/ "Win7 VBox VM Before Resize"
[2]: http://farm4.static.flickr.com/3270/5767015885_22f73b1714_m.jpg
[3]: http://www.flickr.com/photos/gorauskas/5767015957/ "GParted Step 1"
[4]: http://farm4.static.flickr.com/3332/5767015957_9f81947a7f_m.jpg
[5]: http://www.flickr.com/photos/gorauskas/5767558446/ "GParted Step 2"
[6]: http://farm4.static.flickr.com/3602/5767558446_cb91feb79a_m.jpg
[7]: http://www.flickr.com/photos/gorauskas/5767558500/ "GParted Step 3"
[8]: http://farm4.static.flickr.com/3251/5767558500_ac1e56e8ed_m.jpg
[9]: http://www.flickr.com/photos/gorauskas/5767016165/ "Win7 VBox VM After Resize"
[10]: http://farm3.static.flickr.com/2716/5767016165_e390a0ea15_m.jpg

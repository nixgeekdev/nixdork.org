---
title: 'Install Brother HL-2270DW Printer on Debian Jessie'
slug: 'install-brother-printer-on-debian-jessie'
date: 2015-04-03T18:54:28-08:00
tags: ['linux']
---

I have a Brother HL-2270DW laser printer. Here's how to install support for it
in Debian Jessie linux.

## Install CUPS

First you need to install CUPS, the Common Unix Printing System, with the
following command:

    sudo apt-get install cups

Next make sure that the CUPS service is up and running:

    systemctl status cups

## Install the printer drivers

You will next need to get the Brother printer drivers from their website. Follow
these steps:


1. Go to [http://support.brother.com/g/b/countrytop.aspx?c=us&lang=en](http://support.brother.com/g/b/countrytop.aspx?c=us&lang=en)
2. Click on _Downloads_
3. Search for _HL-2270DW_ (my current printer)
4. Select _Linux_ for _OS Family_
5. Select _Linux (deb)_ for _OS Version_
6. Click on _Driver Install Tool_ for _Printer Driver_
7. Agree to the EULA and Download
8. Save it to a folder on your HDD and remember it
9. Open a terminal window and go to the folder where you saved the printer driver
10. Decompress the archive with

        gunzip linux-brprinter-installer-*.*.*-*.gz

11. Become root by running the following command

        sudo -s

11. Install the printer driver with the following command

        bash linux-brprinter-installer-*.*.*-*

12. For `Input model name` enter `HL-2270DW`
13. For `You are going to install following packages. OK?` enter `y`
14. For Brother License Agreement `Do you agree? [Y/n]` enter `y`
15. For GPL `Do you agree? [Y/n]` enter `y`
16. Download of `deb` package and installation will start.
17. for `Will you specify the Device URI?` answer `n`
18. for `Test Print?` answer `n`
19. Hit Enter/Return key.
20. You are done with the Driver installation

## Configure CUPS to use the printer

The final step of this process is to configure CUPS to use the new
printer. Follow these steps:

1. Open a web browser to [http://localhost:631/](http://localhost:631/)
2. Click the _Administration_ tab then click the _Add Printer_ button.
3. Select _IPP_ from the list.
4. In the _Connection_ field, type

        ipp://THE_PRINTER_IP/ipp/port1

5. In the next form, give the printer a unique name (no spaces and the name be must unique from any identical printers), and select _Brother_ from the printer make field.
6. Select _Brother HL2270DW for CUPS (en)_ from the list of drivers
7. Configure the default options on the next page to your liking
8. Set _Duplex_ to _DuplexNoTumble_ for double-side printing
9. Set _TonerSave_ to on to enable toner saving

That's it. Enjoy your new printer.

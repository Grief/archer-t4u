archer-t4u
==========
DKMS module for TP-Link AC1300 Wireless Dual Band USB Adapter aka Archer T4U and kernel 4.8.1-4.10

What's that?
------------
This is yet slightly another version of the Realtek 8812 driver. 
**The driver is supposed to be used only with Archer T4U V1 device and the latest (4.8.1-4.10) kernel only.**
I took the drivers which are provided by TP-Link on the support site and fixed them to work with the latest kernel.

Why did you make it if there are tons of versions already?
----------------------------------------------------------
None of them were working for me, sad but true.
I've upgraded my Ubuntu up to 16.10 which includes kernel 4.8.0 and the previously working driver stopped to work.
I didn't find a way to fix it.
Instead, I grabbed the official drivers and applied changes on my own.
You can look through the commit history, changes were pretty trivial.
I think that having one specific driver for the device is better than trying to support the ultimate driver for all Realtek-based devices.

Does it work?
-------------
Like a charm! Both 2.5GHz and 5GHz work, the connection becomes established in a split second and it handles connections/disconnections of both network and usb smoothly.
However, I found two minor issues:

* Driver spams to dmesg a lot.
* Once, I observed crash on usb disconnection but it continued to work when plugged in again.

Ok, how to install it?
------------------
The same as any DKMS module:
::
  sudo git clone https://github.com/Grief/archer-t4u.git /usr/src/archer-t4u-4.8.1
  sudo dkms add archer-t4u/4.8.1
  sudo dkms install archer-t4u/4.8.1
  reboot

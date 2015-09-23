Primarily developed for the OSx86 community, but should be useful to real mac owners as well.

This is an Intel SpeedStep driver for Mac OS X which supports a much wider range of CPUs and motherboards than the stock AppleIntelCPUPowerManagement kext.

**12 Feb 2010**
This project has now been deprecated in favor of [VoodooPower](http://code.google.com/p/voodoo-power/). Further updates to the kernel extension might not be available. VoodooPower offers better support for newer processors and is actively developed. Everyone is advised to switch to VoodooPower (unless you need manual frequency/voltage control).

**14 June 2009**
A new version 1.4.9 is now available from the Downloads section. Please check [changelog](http://code.google.com/p/xnu-speedstep/wiki/Changelog) for what's new.

**Important**: The v1.4.5 beta is NOT recommended for use by most users as it causes kernel panics.

**22 Nov 2008**
An experimental v1.4.5 is available now. It will try to auto-create a pstate list for you if your ACPI does not return the pstate table. This should allow you to use the kext if earlier you received "Error getting PState table from ACPI". The autothrottler's target CPU load can now also be configured in the Info.plist file.

Please test and report back in the forum or file bug reports on the Issues tab.

**24 Oct 2008**
Auto-throttle is here! The v1.4.0 of the kext now has in-built auto-throttling, which means you no longer have to use any SpeedStep GUI - just install the kext and off you go! Check [AutoThrottle](AutoThrottle.md) for more info.

AMD support is planned for the near future.

Note: There is a fork of this project created by Superhai (link on the right sidebar). This may work better for a lot of newer CPUs, however Pentium M and similar processor owners are advised to continue using the one found on this page.


The discussion forum for questions/support is :  http://forum.insanelymac.com/index.php?showforum=163

### Contributions ###

**[Click here to donate](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=1123935)** (via Paypal)

A few people have contacted me to ask how to donate, so I have put up a link to my Paypal account here. Feel free to contribute any amount you wish. Your contributions are highly appreciated!


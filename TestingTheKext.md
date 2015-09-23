## What to test ##

  1. That you can actually switch CPU speed
  1. Whether your timing is stable (ie. OSX UI/animations should be smooth, not stuttering in audio)
  1. Test whether you can still sleep and then resume - if your sleep/resume worked before

## How to test ##
Most of the testing is done in the command line. There are GUI apps available for regular use, get them from the Downloads page.

To see which frequencies are available:
```
sysctl kern.cputhrottle_freqs
```

To switch frequency:
```
sudo sysctl -w kern.cputhrottle_curfreq=YYYY
```
(replace YYYY with what you want from the list you got. You can also set a single digit number directly which is the frequency (pstate) number: 0 is highest speed, 1 is next lowest etc.

Similarly for kern.cputhrottle\_curvolt. However keep in mind you should not mess with voltages if your processor with factory default voltages performs adequately without overheating.

## Getting debug logs and bug reporting ##
To get debug log messages, first edit the Info.plist file inside the kext and set `DebugMessages` to `<true/>`, then unload/reload the kext and type this in Terminal:
```
sudo dmesg | grep IntelEnhancedSpeedStep
```

If it doesn't work for you, paste on pastebin the output of the above command, and of
```
sysctl machdep.cpu && uname -a
```
then create a new bug report (Issues tab), and attach the URL of the report along with problem description.

To get information about the current freq/voltage and available freq/voltage, type
`sysctl -a | grep throttle`
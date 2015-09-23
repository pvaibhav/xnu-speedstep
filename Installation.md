## What you need ##

To use this kext, you need:
  * Mac OS X (tested on 10.5, should work on 10.4)
  * Any kernel including vanilla, sleep or speedstep
  * A SpeedStep-capable Intel CPU (no AMD, no Celeron M)

## How to install ##
  1. Download the kext from the Downloads page. Unzip it.
  1. Use [KextHelper](http://www.cheetha.net/Kext_Helper/Software.html) or [OSx86-Tools](http://pcwizcomputer.com/osx86tools/) to install it

Alternatively, you can use the command-line to install it.
  1. Open Terminal.app (Applications > Utility)
  1. Navigate to the folder where you unzipped the kext `cd ~/Downloads/IntelEnhancedSpeedStep_1.3.2/`
  1. Type the following:
```
sudo cp -R IntelEnhancedSpeedStep.kext /System/Library/Extensions
sudo chown -R root:wheel /System/Library/Extensions/IntelEnhancedSpeedStep.kext
sudo chmod -R 755 /System/Library/Extensions/IntelEnhancedSpeedStep.kext
sudo touch /System/Library/Extensions
```
  1. Then, reboot.

## How to load/unload without installing ##

You can use `kextload` or `kextunload` to load or unload the kext temporarily. Instead of putting it in /System/Library/Extensions, just keep it anywhere else (/tmp is a good place). Change the permissions/owner using the above commands. Then `kextload /tmp/IntelEnhancedSpeedStep.kext`.

## Now what? ##

Now refer to the TestingTheKext page to begin using/testing it!
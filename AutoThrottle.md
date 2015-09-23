# Introduction #

As of v1.4.0 of the kext, automatic throttling of CPU frequency and voltage is available. All you have to do is install the kext and let it do its job quietly in the background. You don't need any GUI app to control the auto-throttling.

# Usage #

Simply download and install the kext.

If you are using any speedstep gui like DCPUManager or tuxx SpeedStep.app, _please deactivate them, or put them in Manual mode_. Otherwise it will interfere with the kext's auto-throttling. If you put these apps in Manual mode, you can still see the frequencies that the kext is choosing.

# Details #

The auto-throttle works in a slightly different way than the GUI apps or the other speedstep drivers. There is no up/down stepper thresholds. Instead, there is a 'target CPU load'. When the CPU load goes above this target, an appropriate speed is calculated, and the CPU is stepped directly to that P-state. In other words, there is no gradual step up/down. The timer is also adaptive - in the lowest P-state (ie. lowest speed), the timer runs slowly. Once there is a p-state switch, the next check happens sooner, depending on the speed we switched to. This means at higher speeds, we check more often whether we can step back down or not. This means the throttler is quite conservative usually, but still steps directly to the proper frequency under load, giving a good performance also.

This algorithm means there is almost nothing to configure! There is no need to mess with up/down thresholds or timer frequencies. The target load defaults to 30%. If you want to make it more or less conservative, you can change this to higher or lower. A higher target load means the throttler will tolerate a higher load, and will switch to a more conservative (ie. slower) if needed. A lower target load means the throttler will switch more aggressively and to higher speeds. Tune it if you want, although a setting of about 30% was found to be quite enough.

You can set the target load using this command in Terminal:
```
sudo sysctl -w kern.cputhrottle_targetload=XY
```
where XY is your preferred load in %. You cannot specify more than 95% here.

If you want to change the default CPU load, edit the Info.plist and change the **TargetCPULoad** key to whatever you prefer.

## Latching the CPU speed ##

It is possible to set the CPU speed to a fixed frequency. You might want to do this to reduce heat and power consumption (by latching to lowest freq) or to increase audio/gui performance (by latching to highest frequency). To do this, disable auto-throttle first, and then set to whatever speed you want:
```
sudo sysctl -w kern.cputhrottle_auto=0
sudo sysctl -w kern.cputhrottle_freq=XYZ
```

Replace XYZ with the frequency (in MHz) that you want. The kext will choose the closest frequency supported by your processor.
### 1.4.9 ###

  * Fixed panic when trying to automatically create a P-State table on systems with broken ACPI implementation.
  * Added ability to check for kernel boot flag "-autopstates" to force automatic creation of PState table on any system (useful if Info.plist has incorrect PState table preventing boot up)
  * Modified auto-throttle algorithm to be more responsive for high-performance tasks
  * Now waits on IOCPU resource before starting auto-throttle, so that it works when loaded as Root
  * Set the OSBundleRequired property to Root allowing the kext to load very early in the boot process and also in single-user modes

### 1.4.5 ###
  * "Error getting PState array from ACPI" - if you get this error with older versions, this new version will try to create a pstate table for you based on some heuristics. It is not optimal, but will give you a headstart. Later you can fine-tune the pstate table yourself.
  * Info.plist has a new key "TargetCPULoad" currently set to 30%. Change it to whatever you want to be the default.
  * Should also fix the incorrect (high or -ve) cpu frequency problem.

### 1.4.0 ###
  * Auto-throttling support. Read AutoThrottle
  * Misc. bugfixes.

### 1.3.2 ###
  * fix a bug which displayed incorrect current frequency value when using n/2 bus ratio
### 1.3.1 ###
  * fixed certain issues with <1ghz support
### 1.3 ###
  * N/2 bus ratio support, should provide <1GHz pstates to most people. Note that if you have sse2, this will be enabled ONLY if you are using a kernel which supports <1ghz properly. Currently the only such kernel is my kernel 9.4 which is not released yet. :-)
  * Excessive debug messages are now removed. Should fix stuttering while changing frequency
  * Added extra IODelay after switching pstate so that sysctl displays the new values. This should make people happier.
  * Minor internal fixes.
### 1.2.2 ###
  * Better kernel feature detection.
  * Better clock recalibration.
### 1.2.1c ###
  * Kernel feature autodetection, override via Info.plist key "KernelFeatures" in IOKitPersonalities. Set to -1 for autodetect (only works with new kernels which are NOT out yet), 0 = no speedstep,1ghz+, 1=speedstep kernel,1ghz+, 2=speedstep kernel,less than 1ghz support.
  * No more phantom PStates (e.g 2401 mhz)
  * Default Pstate during bootup/load, set DefaultPState key in Info.plist, -1=no default, 0=pstate0 is default etc.
  * Doesn't allow <1 ghz throttling unless patched kernel supports it (vanilla/sleep kernels dont)
### 1.2.0 ###
  * Added delay for latency while switching pstate - should fix people not being able to switch frequencies consistently
  * Undervolting! New sysctl key kern.cputhrottle\_curvolt to change the current voltage. Setting will be remembered for that pstate.
  * Added sysctl key kern.cputhrottle\_ctl for direct changing of fid/vid: only for testing!! Settings will not be remembered
  * Load PState table from kext's info.plist! For those who get "There was an error getting Pstate table from ACPI". To use this, open the kext's Info.plist in property list editor. Expand IOKitPersonalities/IntelEnhancedSpeedStep and you will see PStateTableDisabled. It is an array of arrays. Each element is one pstate. Each pstate has 2 elements, first is the frequency in MHz and 2nd is voltage in mV. If you change the name of the array to PStateTable, it will be loaded by the kext instead of autodetecting via ACPI. NO error checking so make sure it's valid for your CPU.
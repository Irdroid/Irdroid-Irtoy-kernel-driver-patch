# Irdroid-Irtoy-kernel-driver-patch
 Patch for Irtoy/Irdroid new Kernel Driver - allow irrecord to function properly and record remote controls.
 The current (Linux Kernel 5.16) Irtoy/Irdroid driver is not sending start/end of signal markers and therefore it isnt possible to record any signal with Lirc's irrecord tool (The tool is complaining that it couldnt find GAP) . The patch in this repository addresses that issue.

# Steps to reproduce the problem:

1. Make sure lircd is not running and the kernel driver is loaded and Irtoy / Irdroid inserted
2. issue irrecord --disable-namespace in the terminal
3. Try to record any of your existing remotes, such as a TV Remote
4. Irrecord will complain that it couldn't find GAP and the output will be zeros in the resulting remote control lircd.conf file.

# Steps to apply the Patch:
- Download your kernel source
- cd into kernel_source/drivers/media/rc/
- Download the patch
- apply the patch with patch ir_toy.c < Irtoy_Irdroid_irrecord_fix.patch

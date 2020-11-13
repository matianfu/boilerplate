# Name

UCM stands for USB-based Compute Module.

# Vision

The concept of Computer-on-Module or compute module has been around for years. 

Some modules are implemented as minimal system, consisting of PMU, CPU, and a storage device, such as eMMC. Others may incorporate more features, such as the wifi/bt combo for easy to use. Intel even developed a Compute Card with sophiscated interface and form factor. Unfortunately this effort is abandoned last year.

All those efforts are good examples of modular design, reusing engineering efforts and reducing total pcb cost in general. 

However, those modules and their extension boards can seldom be used interchangeably, because almost every module has its own interface design, a unique combination of I/Os on its (soc) platform. 

Now, with the increasing popularity and performance of USB-C, and especially [USB.org's efforts](https://www.usb.org/sites/default/files/D1T1-3%20-%20USB4%20System%20Overview.pdf) to unify various existing interfaces, it is possible that in future, a compute module may have only single USB-C interface, leaving all jobs of power delivery and application-specific i/o to the hub or hubs.

This document describes this vision and a basic implemention of such a system.

# CM

The Compute Module should have a USB-C receptacle, or equivalent internal connector. On this interface, it acts as a sinking host for normal operation.

Operationally it should support Debug Accessory Mode and act as a TS (Testing System). When the system is put into this mode, it should put the CPU into USB firmware download mode, and connect the corresponding USB D+/D- signal to the port. This may or may not be the USB port used in normal operation. If they are the same port, the port supports OTG or DRD.

# UCM Hub

The UCM hub connects to CM with a plug or captive cable. According to USB-C specification, this is the only way to let the sink device detect pull-up on both CC lines.






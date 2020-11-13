# Name

UCM stands for USB-based Compute Module.

# Vision

The concept of Computer-on-Module or compute module has been around for years. 

Some modules are implemented as minimal systems, consisting of PMU (Power Management Unit), CPU, RAM, and storage devices, such as eMMC. Others may incorporate more features, such as the wireless module. Intel even developed a Compute Card with sophiscated interface and form factor. Unfortunately the effort was abandoned last year.

All those efforts are good examples of modular design, reusing engineering efforts and reducing total pcb cost in general. 

However, those modules and their extension boards can seldom be used interchangeably, because almost every module has its own interface design, a unique combination of I/Os on its (soc) platform. 

Now, with the increasing popularity and performance of USB-C, and especially [USB.org's efforts](https://www.usb.org/sites/default/files/D1T1-3%20-%20USB4%20System%20Overview.pdf) to unify various existing interfaces, it is possible that in future, a compute module may have only single USB-C interface, leaving all jobs of power delivery and application-specific i/o to the hub or hubs.

This document describes this vision and discusses a few details of such a system.

# UCM

The UCM should have a USB-C receptacle, or a equivalent internal connector. On this interface, it acts as a sinking host for normal operation.

Optionally the UCM should support USB-C Debug Accessory Mode and act as a TS (Testing System). When Debug Accessory Mode is detected during power up, the CPU should be put into USB Boot mode and corresponding USB D+/D- are connected to the port. Of course this requires a dedicated MCU for USB-C CC/PD control. In Debug Accessory Mode, the UCM is a sinking device. The USB port used in Debug Accessory Mode may or may not be the same port used in normal operation mode. If they are the same one, the port should support OTG/DRD mode. If they are not, a 2:1 analog USB switch is required.

# UCM Hub

The UCM hub should connects to CM with a plug or captive cable. Otherwise, the Debug Accessory Mode could not be supported.

The UCM hub should support sinking host with `dr_swap`. After the success of this command, the UCM hub connects D+/D- and SSTX/SSRX signals to the upstream port of internal hub chip.

## wifi/bt

to be done




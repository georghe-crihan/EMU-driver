<img align="right" width="400" src="E-MU_0404_USB.jpg"/>

EMU-USB driver
=============

I needed the driver for Mountain Lion (10.8), EMU0202, hence the fork.
In addition, I wanted to free myself from the perpetually changing xcode SDK.
There's the Makefile, alowing to build under various xcode versions.

OSX driver for Creative Labs EMU USB

* Tested on Mavericks, Yosemite, El Capitan and Sierra.
* All sample rates are supported both for record and playback: 44.1, 48, 88.2, 96, 176.4 and 192 kHz
* I can only test on EMU0404 USB as I have no other EMU devices. But users reported it works also on EMU0202, EMU0204 and Tracker Pre USB.
* Midi support.

Please notify me how my driver works on other EMU USB devices.

Topics
========
 * <a href="Install.md">Installation, Usage, Uninstall</a>
 * <a href="Latency.md">Adjusting the latency</a>
 * <a href="FAQ.md">frequently asked questions</a> 
 * <a href="TechSpecs.md">Technical Specifications</a>
 * <a href="Developer.md">Developer notes (build from source code, etc)</a>
 * <a href="Acceptance.md">Acceptance Test procedure</a>



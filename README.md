# Langstone SDR Transceiver

This is an experimental project to produce a simple VHF, UHF and Microwave SDR Transceiver operating on SSB CW and FM.
This was inspired by the very successful Portsdown Amateur Television system created by the British Amateur Television Club.
This is not yet a finished project but more of a demonstration of what can be done. 

Currently only one set of hardware is supported:-

Raspberry Pi 4
Official Raspberry Pi 7" touchscreen.
Adalm Pluto SDR Module
USB Audio module
USB Scroll mouse

To build a complete functional transceiver you will need to add suitable filters, preamplifiers and power amplifiers to the Adalm Pluto. 

All control is done using the touchscreen.
Tuning uses the mouse scrollwheel. The mouse left and right buttons select the tuning step. Mouse movement is not used. 
The intention is to eventaully make use of the mouse hardware to make a proper tuning knob and panel controls. 
Microphone input and headphone output uses the USB audio device. (a couple of pounds on Ebay)

The software consists of two parts. The SDR itself uses a python GNURadio Flowgraph which can be created on a PC running GNUradio companion. This Python program is manually edited so it can be controlled by the GUI part of the software. This is written in C and communicates with GNURadio using a Linux Pipe. 



# Installation for Langstone Transceiver

The preferred installation method only needs a Windows PC connected to the same (internet-connected) network as your Raspberry Pi.  Do not connect a keyboard or HDMI display directly to your Raspberry Pi.

- First download the 2019-26-09 release of Raspbian Buster Lite on to your Windows PC from here  https://downloads.raspberrypi.org/raspbian_lite/images/raspbian_lite-2019-09-30/2019-09-26-raspbian-buster-lite.zip

- Unzip the image and then transfer it to a Micro-SD Card using Win32diskimager https://sourceforge.net/projects/win32diskimager/

- Before you remove the card from your Windows PC, look at the card with windows explorer; the volume should be labeled "boot".  Create a new empty file called ssh in the top-level (root) directory by right-clicking, selecting New, Text Document, and then change the name to ssh (not ssh.txt).  You should get a window warning about changing the filename extension.  Click OK.  If you do not get this warning, you have created a file called ssh.txt and you need to rename it ssh.  IMPORTANT NOTE: by default, Windows (all versions) hides the .txt extension on the ssh file.  To change this, in Windows Explorer, select File, Options, click the View tab, and then untick "Hide extensions for known file types". Then click OK.

- Connect the 7" touchscreen display, USB mouse, USB Sound Card, and Pluto now.   Power up the RPi with the new card inserted, and a network connection.  Do not connect a keyboard or HDMI display to the Raspberry Pi. 

- Find the IP address of your Raspberry Pi using an IP Scanner (such as Advanced IP Scanner http://filehippo.com/download_advanced_ip_scanner/ for Windows, or Fing on an iPhone) to get the RPi's IP address 

- From your windows PC use Putty (http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) to log in to the IP address that you noted earlier.  You will get a Security warning the first time you try; this is normal.

- Log in (user: pi, password: raspberry) then cut and paste the following code in, one line at a time:

```sh
wget https://raw.githubusercontent.com/g4eml/Langstone/master/install.sh
chmod +x install.sh
./install.sh
```

The initial build can take some time, however it does not need any user input, so go and make a cup of coffee and keep an eye on the touchscreen.  When the build is finished the Pi will reboot and start-up with the Langstone Transceiver



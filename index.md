pyBus
=====

iBus interface for my E46 BMW written in Python
This is to be used with the USB interface which can be acquired from [Reslers.de](http://www.reslers.de/IBUS/)

The software expects MPD to be working on whatever it is installed on (I use a Raspberry-Pi, if you are interested in doing the same, check out the project page on my blog for a guide! [HEAH](http://blog.danielvagg.com/blog/?page_id=25))

## Overview
There are 2 main components:  
**pyBus.py** - Interfaces with the iBus to emulate a CD-Changer as well as other devices:
* Loads up a music library from a memory stick.
* Emulates a CD changer with appropriate signals and responses
* Plays music over the car speakers
* Can be controlled using radio controls and steering wheel controls as you would expect.
* Displays track info on the standard radio LED display (not the fancy screens)

**pyBus_web.py** - Web-Server which creates a web-page that allows a user to:  
* Play/Pause
* Next/Previous
* Modify Playlist

### Useful links
http://linux.die.net/man/5/mpd.conf   
http://miro.oorganica.com/raspberry-pi-mpd/   
http://web.comhem.se/bengt-olof.swing/ibusdevicesandoperations.htm   

### Warning
The software is not completely finished, and regardless of its state, I shall not accept liability for any damage done by this software (though it is next to impossible due to the nature of the iBus).

### Architecture/Operation
I am in the process of illustrating this. At the very least I should let you know there are multiple threads involved in this.

## Pre-Requisites
* python, mpd, python-setuptools, mpc (mpd CLI, useful for testing)
	* `apt-get install python python-setuptools mpd mpc`
* **Python modules:** termcolor, web.py, python-mpd, pyserial, probably more
	* `easy_install termcolor web.py python-mpd pyserial`
## How to use
* Install the prerequisites above. There may be more, feel free to leave a comment letting me know which one.
* Ensure music is available at /music and that mpd is configured to read from there (best test mpc using mpc prior). NOTE: I use a little bit of BASh to mount my memory stick to /music on boot up. 
* There is also a requirement for a folder: (/music/pyBus). Logging will go in this folder, which is useful for debugging away from the RPi.

* Plug in iBus USB device
* Run: `./pyBus.py <PATH to USB Device>`
	* E.g. `./pyBus.py /dev/ttyUSB0`

# vnc_virtual_display_linker
### A Python script to create a second virtual monitor for connecting with VNC

This script will let you connect an external device to your X11 server as a second monitor through VNC  
i.e. use your tablet to extend your desktop

I have it working using Xubuntu 16.04 and an Android phone (Samsung Galaxy A3 2017)

## INSTALLATION:
`pip install dotmap`  
`sudo apt install x11vnc`

## USAGE
- place the script anywhere
- you might have to grant exec permissions: `chmod +x vnc_virtual_display_linker.py`
- launch the script `./vnc_virtual_display_linker.py`
- on the menu:
  - press `a` to activate the adbc connection (to use it via USB. See ADB SUPPORT)
  - press `s` to start the VNC server with the default configuration
  - enter a password
    - `ctrl-c` to stop the server
  - follow the instructions on the screen for more functionalities

Once the server has started, on your device:
- launch a VNC client like [bVNC Free](https://play.google.com/store/apps/details?id=com.iiordanov.freebVNC&hl=it)
- configure the ip address of the server and the password you used while installing x11vnc
- connect and enjoy your second screen!

## ADB SUPPORT
You should be able to connect most Android tablets/phones with an USB cable to the VNC server thanks to the ADB platform.
Because of smaller latency, I would recommend you to connect your device via this way.

First, you need to install the proper tools:  
`sudo apt install adb android-tools-adb android-tools-fastboot`

Then you have to:
- connect your device (i.e. the tablet) to the PC with an USB cable 
- turn on USB debugging on your device
- activate the ADB support in the vnc_virtual_display_linker menu
- connect with your device to `localhost` as server address

## CHANGES
First of all, thanks to [mrenrich84](https://github.com/mrenrich84) for this great tool :).

To get it running, I needed to change the port for the second monitor, because my laptop has no VIRTUAL port. I've mapped it to the VGA port.
If your laptop doesn't have a VGA port or you want to map the second monitor to another port, change the "VIRTUAL_MONITOR_PORT" variable to one of the port your machine provides.

Your laptop can show your the available ports via:
`xrandr`

Choose one of the disconnected ports and set the variable to the name of that port.

Some additionally minor changes:
- you need to enter a password now to start the server
- the currently open second monitor will be destroyed when you start a new monitor
- the second monitor will be destroyed when you quit the script
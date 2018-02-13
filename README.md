# Setup
The following sections explain the required steps to prepare the PC/Mac and the Raspberry Pi

## Table of Contents  
#### 1. [Setting up your personal computer](#pcmac)    
#### 2. [Setting up your Raspberry Pi](#rpi) 
#### 3. [Remote access to Raspberry Pi through VNC](#vnc) 

<a name="rpi"/>

## RPi
### Preparing the Raspberry Pi SD card
1.	Download Raspbian OS image from https://www.raspberrypi.org/downloads/raspbian/
2.  Burn it to the SD card using DiskImager https://sourceforge.net/projects/win32diskimager/

### Initiating the RPi
#### Running the Raspberry Pi with a monitor
1.	Connect the RPi to a monitor, mouse, keyboard, and start the RPi
4.	From the network icon on the desktop toolbar connect to a WiFi network
5.	Open Terminal
6.	Run ifconfig to find the RPi’s IP address
7.	Type in sudo apt-get update
8.	Type in sudo apt-get upgrade

#### Running Raspberry Pi Headless (without a monitor)
This section will only work if you burned Raspbian onto the SD card, and may not work if you started with Noobs (the OS already burned on the SD card that comes with the RPi)
1.	Plug the SD card reader into your computer
2.	Open the cmdline.txt file on the main root of the SD card and append the following
```
ip=192.168.100.200::192.168.100.1:255.255.255.0:rpi:eth0:off
```
Where `192.168.100.200` is the IP address, `192.168.100.1` is the network gateway, and `255.255.255.0` is the network mask. You are free to change the IP address to any value as long as you choose one on the same subnet at the you set your computer to in Step 8.
3.	Plug the SD card back into the RPi, then connect the RPi to your computer using an ethernet cable.
4.	Right-click the network icon on your computer's toolbar and choose "Network and Sharing Center".
5.  From the side menu, choose "Change adapter settings".
6.  Right-click the ethernet network adapter, and choose "Properties"
7.  In the scroll-down menu, choose "Internet Protocol Version 4 (TCP/IPv4) and select "Properties"
8.  Select "Use the following IP address", and set the IP to `192.168.100.201`, subnet mask to `255.255.255.0`, and default gateway to `192.168.100.1`.

Finally, test the conneciton by opening Windows Command Line and typing in
```
ping 192.168.100.200
```

### Connecting through SSH
The follwoing commands will work on Mac machines only. To SSH from Windows, use PuTTY (http://www.putty.org/)

6.	Type in
```
ssh pi@x.x.x.x
```
where x.x.x.x is the IP address of your Pi
7.	Enter raspberry when asked for the password
8.	You now have access to the Pi through its terminal

<a name="vnc"/>

## VNC
### Raspberry Pi
### Download realVNC
From terminal, run the following commands
```
sudo apt-get update
sudo apt-get install realvnc-vnc-server realvnc-vnc-viewer
```
### Enable VNC
From terminal, run the following command
```
sudo raspi-config
```

Navigate to **Interfacing Options**, then scroll down and select **VNC > Yes**.

Restart
```
sudo reboot
```

### PC
Install VNC viewer from https://www.realvnc.com/en/connect/download/viewer/

### Usage
Open VNCViewer on your computer, and type the IP address of the Raspberry Pi followed by port `5900` e.g. `x.x.x.x:5900`, then enter the Raspberry Pi’s username and password
![Screenshot](/images/vnc2.png?raw=true "Login")


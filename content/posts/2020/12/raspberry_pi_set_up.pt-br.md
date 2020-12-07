+++
title =  "Setting up a brand new Raspberry Pi"
date =  2020-12-07T18:00:00+01:00
description = ""
author = "Odinei Alexandre"
+++

### Installing Raspberry Pi OS ###

* Insert the SD card on your computer
* Download raspbery Pi Imager from https://www.raspberrypi.org/software/
* Through Raspberry Pi Imager, format the SD card and install the OS.

### Setting up Network ###
```
sudo service dhcpcd status
```
* Open your SD card and go to /boot
* Create a file called wpa_supplicant.conf. We will use this file to add the network details, including SSID and Password, as shown below:

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=BR
network={
    ssid="YOURSSID"
    psk="YOURPASSWORD"
    scan_ssid=1
}
```

### Enabling SSH ###

* Create an empty SSH file, without extension. This file will be used during the boot to enable the SSH connection.

### Testing your Raspberry ###
* Now you can remover the SD card from your computer and insert it on your Raspberry Pi
* Connect your Raspberry Pi in the energy outlet
* Run the command arp -a to identify the Raspbery Pi IP Address
* Stabilish the connection using SSH
* If you noticed that the connection was not performed, connect a lan network into your Raspberry
* Run command arp-a again to identify the IP Address and connect through it using SSH
* Once connected, run the command below to identify what could be wrong with your wpa_supplicant file

```
sudo wpa_supplicant -c /etc/wpa_supplicant/wpa_supplicant.conf -d -iwlan0
```

* Fix the errors and restart your Raspberry

```
sudo reboot
```
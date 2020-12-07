+++
title =  "Setting up a Raspberry Pi Static IP Address "
date =  2020-12-07T19:20:00+01:00
description = ""
author = "Odinei Alexandre"
+++

### Pre Requisites ###

#### Check the DHCP status #####
```
sudo service dhcpcd status
```

If it is not activated, run the command below:

```
sudo service dhcpcd start
sudo systemctl enable dhcpcd
```

#### Identify Router IP Address ####

```
netstat -nr | grep default
```

#### Identify DNS Server ####

```
sudo vim /etc/resolv.conf
```

#### Adding the static IP Address ####

```
sudo vim /etc/dhcpcd.conf
```

```
interface <wlan0 or eth0>
static ip_address=<STATIC_IP_ADDRESS>/24
static routers=<ROUTER_IP_ADDRESS>
static domain_name_servers=<DNS_IP_ADDRESS>
```

#### Reboot ####

```
sudo reboot
```
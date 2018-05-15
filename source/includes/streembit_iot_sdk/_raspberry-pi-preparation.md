## Raspberry Pi - Preparation

Here you will find the instructions and some additional links to setup the Raspberry Pi ready to install and run the Streembit CLI application.  You may prefer to attach separate screen and keyboard to the R-Pi instead of using SSH to connect to it.

### Install the Raspberry PI

Burn the latest Raspbian OS to a micro SD card.

[https://www.raspberrypi.org/documentation/installation/installing-images/](https://www.raspberrypi.org/documentation/installation/installing-images/)

Add an ssh file to the Raspbian boot image at the SD card. Step 3 in this tutorial:
[https://hackernoon.com/raspberry-pi-headless-install-462ccabd75d0](https://hackernoon.com/raspberry-pi-headless-install-462ccabd75d0)

### Login via SSH and configure the device

```json
see shell code
```
```shell
sudo raspi-config
```
Login to the Raspberry PI via SSH using your Linux/MAC SSH client or PUTTY on Windows. If you don't have access to the router to lookup the IP address, use the Advanced IP Scanner application to find your Raspberry PI device [www.advanced-ip-scanner.com](http://www.advanced-ip-scanner.com).
The default **user name**: *pi*, **password**: *raspberry*.

Once you logged in via SSH:
  1. Enable SSH: select Interfacing Options. Navigate to and select SSH, and select "Yes".
  2. Enable serial port: select "Interfacing Options". Navigate to "Advanced" and select "Options/Serial". You will be prompted with the “Would you like a login shell to be accessible over serial?” question. Select "No". Then you will be prompted "Would you like the serial port hardware to be enabled?". Select "Yes". Select "Finish" and reboot the device.
  3. Refer to the "For latest Jessie version" section at [https://hallard.me/enable-serial-port-on-raspberry-pi/](https://hallard.me/enable-serial-port-on-raspberry-pi/)

```json
see shell code
```
```shell
ls -l /dev
```

Check the available serial ports and serial port aliases.
ttyS0 should be listed in dev directory

### Install the latest Nodejs

```json
see shell code
```
```shell
# Install with package manager
curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt-get install -y nodejs
```

**Option 1**

Install Nodejs with APT package manager


```json
see shell code
```
```shell
# Install with NVM
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.0/install.sh | bash

# Now close you terminal and then open it up again
# to make nvm command available
nvm install --lts
```

**Option 2**

Install Nodejs with NVM (Node Version Manager)


```json
see shell code
```
```shell
# Install from sources
sudo apt-get update
sudo apt-get install build-essential checkinstall
cd /usr/local/src

# Download the latest Node.js source.
# Substitute 9.10.0 with the latest Node.js version number

sudo tar -xvzf node-v9.10.0.tar.gz
cd node-v9.10.0
sudo ./configure
sudo make install

# when the system completes the downloading and installation procedures,
# make sure you have nodejs installed

node -v

# Update npm to the latest version
sudo npm install -g npm
```

**Option 3**

Install Node.js from source

The version should be at minimum 9.10.0


### Install PM2 process manager

```json
see shell code
```
```shell
# Install pm2 globally
sudo npm install -g pm2
```


### Install git and clone CLI repository

```json
see shell code
```
```shell
sudo apt-get install git

# cd to arbitrary folder on which you have r/w permissions
cd /FOLDER/OF/DEPLOY
git clone https://github.com/streembit/streembit-cli
cd streembit-cli
```


### Connect to a WiFi network

```json
see shell code
```
```shell

# List the available WiFi networks

sudo nano /etc/wpa_supplicant/wpa_supplicant.conf

# Edit the WiFi configuration file

network={
    ssid="YOUR_WIFI_NETWORK"
    psk="WIFI_NETWORK_PASSWORD"
}

ifconfig wlan0

# You should see something that resembles this output

wlan0   Link encap:Ethernet HWaddr 74:da:38:2b:1c:3d
        inet addr:192.168.1.216 Bcast:192.168.1.255 Mask:255.255.255.0
        inet6 addr: fe80::8727:5526:a190:b339/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        RX packets:6917 errors:0 dropped:229 overruns:0 frame:0
        TX packets:2931 errors:0 dropped:1 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:10001000 (9.5 MiB) TX bytes:295067 (288.1 KiB)
```

Set the SSID and WPA-PSK password
If you are connected the "inet addr" should be a 192.168.xxx.xxx IP address

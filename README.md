# Installing Nodejs and Cloud9 IDE on Raspberry Pi 1 B+

## Raspberry Pi and Raspbian
### Requirements
1. Raspberry Pi
2. SD Card
3. USB Keyboard
4. Internet connection via RJ45 Ethernet cable
5. Micro USB power supply

### Installation
1. Download OS from https://www.raspberrypi.org/downloads/raspbian/.
2. Download Etcher from https://etcher.io/.
3. Open Etcher.
4. Select Raspbian image file.
5. Select SD card drive.
6. Click "Flash" to burn OS image on SD Card.

### Setup
1. Put the SD Card on Raspberry Pi.
2. Connect monitor, keyboard and internet cable on Raspberry Pi board.
3. Plug raspberry on the energy.
4. Login on raspbian using pi:raspberry credential.
5. Update raspbian: `$ sudo apt-get update`
6. Open Raspi-Config tool: `$ sudo raspi-config`
7. Choose `Interfacing Options` > `SSH` and enable SSH.
8. Now you can access your Raspberry Pi through SSH from whatever
machine at same network as Raspberry.
9. At Raspi-Config you can optionally choose the `Change Password`
option and choose another password to the pi user.


## Nodejs and NPM
### Installation
```sh
$ cd ~
$ wget https://nodejs.org/dist/v8.1.4/node-v8.1.4-linux-armv6l.tar.xz
$ tar -xf node-v8.1.4-linux-armv6l.tar.xz
$ rm node-v8.1.4-linux-armv6l.tar.xz
$ sudo ln -s /home/pi/node-v8.1.4-linux-armv6l/bin/node /usr/local/bin/
$ sudo ln -s /home/pi/node-v8.1.4-linux-armv6l/bin/npm /usr/local/bin/
```

## Cloud9
### Installation
```sh
$ sudo apt-get install git
$ git clone git://github.com/c9/core.git c9sdk
$ cd c9sdk/
$ scripts/install-sdk.sh # it takes a lot of time :/
```

### Running
```sh
$ cd c9sdk/
$ git reset HEAD --hard # reset to have all clean
$ node server.js -l 0.0.0.0 -p 8080 -a usr:pwd -w /home/pi/ &
```

### Open Cloud9
`http://<RASPBERRY_IP>:8080/ide.html`

PS.: The first two loads of Cloud9 can be a little bit slowly or can have
a broken interface because of additional setups of Cloud9.

### Extra Tip: NoIP
Creating an account on https://www.noip.com/, you can get a free domain
and point this to your exit IP address. With these in hands, you can create
a forward from your router port to point ssh port and other ports running the
services on your Raspberry Pi and access it everywhere through the Internet.

# Initial configuration

---

## Kde screen tearing
Tested for Kubuntu 18.04. Save the following file as /etc/profile.d/kwin.sh

	export __GL_YIELD="USLEEP"

You also want to set kernel parameters at /etc/default/grub (this applies for nvidia users)

	GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"

After, sudo update-grub2 then reboot. 

## TP-Link Wireless Adapter
If you want use a TP-Link wireless adapter or update your wireless dirver:

	sudo apt-get install build-essential linux-headers-generic dkms git
	git clone https://github.com/Mange/rtl8192eu-linux-driver.git
	sudo dkms add ./rtl8192eu-linux-driver
	sudo dkms install rtl8192eu/1.0

If you do not have an internet connection, [download](https://github.com/Mange/rtl8192eu-linux-driver/archive/master.zip) and extract. Then run

	cd Desktop
	sudo dkms add ./rtl8192eu-linux-driver
	sudo dkms install rtl8192eu/1.0

Finish up with

	cd Desktop/rtl8192eu-linux-driver
	make clean

If your machine came with a default driver (i.e. your dongle works without any driver installs), you want to first blacklist the old driver. First, check which driver is being used (lshw -c network). The driver name should be rtl8xxxu. Go to /etc/modprobe.d and create file rtl8xxxu-blacklist.conf
	
	# Do not load the 'rtl8xxxu' module on boot.
	blacklist rtl8xxxu

Now enable the driver that we have installed in /etc/modules. 

	8192eu
	loop

Reboot your machine and check drivers again with lshw -c network.


## Github link
[Github link](http://github.com/uhah229)

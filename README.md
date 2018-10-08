# Initial configuration

---

## Kde screen tearing
Tested for Kubuntu 18.04. Save the following file as /etc/profile.d/kwin.sh

	export __GL_YIELD="USLEEP"

You also want to set kernel parameters at /etc/default/grub (this applies for nvidia users)

	GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"

After, sudo update-grub2 then reboot. 

## Github link
[Github link](http://github.com/uhah229)

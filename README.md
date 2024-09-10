# Karaqu
This repository is primarily used for issue tracking.


## Raspbian Buster Lite installation

sudo raspi-config
  * change password
  * boot / autologin as pi
  * enable ssh

sudo apt-get install git python3-pip

git clone https://github.com/pimoroni/fanshim-python
	cd fanshim-python
	sudo ./install.sh
	cd examples
	sudo ./install-service.sh --on-threshold 65 --off-threshold 55 --delay 2

sudo nano /boot/config.txt
  * at the end of file:
  disable_splash=1

sudo nano /boot/cmdline.txt
  * change to:
    console=tty3

  * at end of line:
    quiet logo.nologo vt.global_cursor_default=0



sudo apt-get install fbi

### copy splash.png to pi-home
scp splash.png pi@192.168.1.148:/home/pi/

sudo nano /etc/systemd/system/splashscreen.service

		[Unit]
		Description=Splash screen
		DefaultDependencies=no
		After=local-fs.target

		[Service]
		ExecStart=/usr/bin/fbi -d /dev/fb0 --noverbose -a /home/pi/splash.png
		StandardInput=tty
		StandardOutput=tty

		[Install]
		WantedBy=sysinit.target

sudo systemctl enable splashscreen



sudo apt-get install --no-install-recommends xserver-xorg x11-xserver-utils xinit openbox

sudo apt-get install --no-install-recommends chromium-browser

sudo nano /etc/xdg/openbox/autostart

	xset -dpms            # turn off display power management system
	xset s noblank        # turn off screen blanking
	xset s off            # turn off screen saver

	# Allow quitting the X server with CTRL-ATL-Backspace
	setxkbmap -option terminate:ctrl_alt_bksp

	# Remove exit errors from the config files that could trigger a warning
	sed -i 's/"exited_cleanly":false/"exited_cleanly":true/' ~/.config/chromium/'Local State'
	sed -i 's/"exited_cleanly":false/"exited_cleanly":true/; s/"exit_type":"[^"]\+"/"exit_type":"Normal"/' ~/.config/chromium/$

	# Run Chromium in kiosk mode
	chromium-browser  --noerrdialogs --disable-infobars --kiosk $DEFIANT_URL


sudo nano /etc/xdg/openbox/environment

	export DEFIANT=https://www.karaqu.com


sudo nano .bash_profile
	# paste in:
	[[ -z $DISPLAY && $XDG_VTNR -eq 1 ]] && startx >/dev/null 2>&1

source .bash_profile


### silences login messages
 sudo touch ~/.hushlogin

sudo nano /etc/systemd/system/getty@tty1.service.d/autologin.conf
	# replace this row; `ExecStart=-/sbin/agetty --autologin pi --noclear %I $TERM` with:
	ExecStart=-/sbin/agetty --skip-login --noclear --noissue --login-options "-f pi" %I $TERM


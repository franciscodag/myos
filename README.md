# Details for setting up Raspis
Copy Raspbian Jessie image
Start Raspi and wait for it to load - will take a while
https://learn.adafruit.com/pi-wifi-radio/raspberry-pi-setup-1-of-3?gclid=CjwKCAiAlfnUBRBQEiwAWpPA6R2wkrojnHjrgsSqo01PdBxUB7MyEEnpcAMZ416P_OuGX1onkYf36BoC4LEQAvD_BwE
1-Expand filesystem
2-Enable I2C
3-Change pw
4-Change Host Name
5-Enable SSH
6-Enable keyboard: United States->with international alternative
7-Enable WiFi:
	sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
	ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
	update_config=1
	network={
		ssid="network_name"
		psk="wifi_pw"
		scan_ssid=1
	}
8-Enable I2C
	sudo nano /etc/modules
	i2c-bcm2708 
	i2c-dev

9-Edit config.txt to add (https://www.youtube.com/watch?v=ga0yDjBWxK0):
	max_usb_current=1
	hdmi_group=2
	hdmi_mode=1
	hdmi_mode=87
	hdmi_cvt 800 480 60 6 0 0 0
10-Download and install screen driver from Git (https://mega.nz/#F!iI9WjThL!VHRNzC44Cxlx7CjIQQJqBQ!SIsTWDZT)
	git clone https://github.com/goodtft/LCD-show.git
	chmod -R 755 LCD-show 
	cd LCD-show/ 
	sudo ./LCD7B-show
11-Installing keyboard:
	sudo apt-get install matchbox-keyboard
	Menu->Preferences->Main Menu Editor->Accesories->Mark keyboard (if it doesn't work, unmark, click ok, then mark again)
cd ~
git clone https://github.com/OpenSprinkler/OpenSprinklerGen2.git
cd OpenSprinklerGen2
sudo ./build.sh ospi

#Set date:
set to Santiago on raspi-config
Set correct NTP server:
	sudo apt-get install ntpdate
	sudo ntpdate -b -s -u cl.pool.ntp.org
	
sudo rpi-update

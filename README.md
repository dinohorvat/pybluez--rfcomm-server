# pybluez--rfcomm-server
<h3>Python Bluez RFCOMM Server (Bluetooth communication)</h3?

<h2>Sending the Raspberry Pi's IP to a client (Mobile phone) over bluetooth</h2>

<h3>Running the server on startup:</h3>
<code>sudo nano /etc/rc.local</code>
<br>
Added this before the exit line (bottom of the script)
<br>
<code>sudo bash -c 'python /YOUR-PATH/rfcomm-server.py > /YOUR-PATH/rfcomm-server.log 2>&1' &</code>


<h3>Full Guide step by step</h3>
Making the bluetooth pairing Raspberry - Phone and sending the Raspberry IP to phone

1) Install the newest Raspbian Stretch image and mount it to Pi
	- https://www.raspberrypi.org/downloads/raspbian/
	- Version I used was released on 2019-04-08
	- Balena Etcher used to flash the SD card and mount the image
  
2) Boot up the Raspberry with HDMI connected

3) Follow the tutorial to setup and make sure to update the software on last step

4) Restart the device

5) Click the Raspberry Logo in upper left toolbar - Preferences > Raspberry Pi Configuration > Interfaces > Enable SSH

6) On your computer open the terminal and ssh to your raspberry device: ssh pi@192.168.0.120

7) Setting up bluetooth settings
	1) sudo apt-get install pulseaudio bluez pulseaudio-module-bluetooth python-gobject python-gobject-2

	2) In /etc/bluetooth/input.conf file, add Enable=Source,Sink,Media,Socket.

	3) In /etc/pulse/daemon.conf file, add ; resample-method = trivial.

	4) In /etc/bluetooth/main.conf file, add Class = 0x00041C.

	5) sudo reboot

8) Making bluetooth auto accept pairing from other devices
	1) sudo nano /etc/systemd/system/dbus-org.bluez.service
	2) change ExecStart=/usr/lib/bluetooth/bluetoothd into ExecStart=/usr/lib/bluetooth/bluetoothd -C
	3) sudo sdptool add SP

9) Clone RFCOMM server into some folder
	git clone https://github.com/dinohorvat/pybluez--rfcomm-server.git

10) Install Pybluez
	1) sudo apt-get install bluetooth libbluetooth-dev
	2) sudo pip install pybluez

11) Making the script run on boot
	1) sudo nano /etc/rc.local 
	2) Added this before the exit line (bottom of the script) 
	   sudo bash -c 'python /YOUR-PATH/rfcomm-server.py > /YOUR-PATH/rfcomm-server.log 2>&1' &

12) sudo reboot

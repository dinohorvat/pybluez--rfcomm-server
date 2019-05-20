# pybluez--rfcomm-server
<h3>Python Bluez RFCOMM Server (Bluetooth communication)</h3?

<h2>Sending the Raspberry Pi's IP to a client (Mobile phone) over bluetooth</h2>

Running the server on startup:
<code>sudo nano /etc/rc.local</code>
Added this before the exit line (bottom of the script)
<code>sudo bash -c 'python /home/pi/smartplay/bluez/bluez/pybluez-master/examples/simple/rfcomm-server.py > /home/pi/smartplay/blink.log 2>&1' &</code>

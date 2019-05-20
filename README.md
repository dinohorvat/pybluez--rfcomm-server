# pybluez--rfcomm-server
<h3>Python Bluez RFCOMM Server (Bluetooth communication)</h3?

<h2>Sending the Raspberry Pi's IP to a client (Mobile phone) over bluetooth</h2>

<h3>Running the server on startup:</h3>
<code>sudo nano /etc/rc.local</code>
<br>
Added this before the exit line (bottom of the script)
<br>
<code>sudo bash -c 'python /YOUR-PATH/rfcomm-server.py > /YOUR-PATH/rfcomm-server.log 2>&1' &</code>

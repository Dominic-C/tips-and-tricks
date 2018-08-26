# Enabling SSH for Ubuntu Mate on startup
* Install Openssh
    * `sudo apt-get update`
    * `sudo apt-get install openssh-server`
* enable ssh
    * `sudo systemctl enable ssh`
    * `sudo service ssh restart`

# Enabling VNC for Ubuntu Mate on RaspberryPi
* Download [link](https://www.realvnc.com/en/connect/download/vnc/raspberrypi/)
* After installation, run the following command to start VNC server on every boot:

`sudo systemctl enable vncserver-x11-serviced.service`

For more commands similar to the one above, refer to [this](https://www.realvnc.com/en/connect/docs/unix-start-stop.html#unix-start-stop)

# Setting up Static IP address on Ubuntu Mate
the quickest and easiest way to do this is to use the GUI.

1. Click on the network icon
2. Click on Edit Connections
3. Click on the wifi channel and click edit
4. Under IPv6 settings, choose Method: Ignore
5. Under IPv4 settings, choose Method: Manual
    * Under addresses in this tab, select add address
    * Set address to a new static IP
    * Set Netmask to 255.255.255.0
    * Gateway is the IP of your router. It can be found with `ip route | grep default`
    * DNS Server is the same as Gateway

run `ifconfig` in the terminal to check if the IP has changed. Disconnect and reconnect to your wifi and observe if the IP address is actually static.
# Networking

## Setting Up a static IP

in `/etc/network/interfaces`, add/modify in these lines

```
# run ifconfig to determine your network interface name
auto eth0
    iface eth0 inet static
    address 192.168.0.2 # can communicate with computers with IP 192.168.0.X
    netmask 255.255.255.0
```

## Setting a LAN port to allow automatic assigning of IP via DHCP

in `/etc/network/interfaces`, add/modify these lines

```
# run ifconfig to determine your network interface name
# assuming your wired LAN interface is named "eth0"
auto eth0
    iface eth0 inet dhcp # router assigns the IP address to your device's ethernet port
```

After editing the interface files, we need to flush out the old IP address

* `ip address flush dev <interface>`. This removes the old IP addresses from the cache

* `ifdown <interface>` brings the network interface down.

* `ifup <interface>` brings the network interface up, enabling the router to assign an IP address to it.

## Communicating between two computers via Ethernet

### Two computers on the same network
* use `ssh` and `scp`
    * ssh syntax: `ssh username@<ip address>`

### Two computers not on any network
* connect an ethernet cable from one computer to the other.
* Assign a static IP on both computer's ethernet ports. Make sure the first 3 fields of the IP are the same in both computers. This will allow communication between the ports.
* we should now be able to use `ssh` and `scp` to communicate between these devices

## Checking speed rating of an ethernet port
* run `ifconfig` to check your network interfaces (ethernet LAN ports should start with "e", wireless LAN starts with "w")
* run `ethtool <interface name> | grep Speed`
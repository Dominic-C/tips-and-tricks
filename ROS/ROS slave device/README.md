# Using ROS across multiple devices
To use ROS across multiple computers, you have to select a device to act as a master, and the rest to act as slaves.

## Set up ROS master computer
quick tip: `export` creates variables in your instance of the shell

This device will be running roscore. On this device, do the following:
* `~$ export ROS_MASTER_URI="http://<ip address of master computer>:11311"`
* `~$ export ROS_IP="<ip address of master computer>"`

## Set up ROS slave computer(s)
The device(s) will be subscribing to roscore from the Master device. Run the following:
* `~$ export ROS_MASTER_URI="https://<ip address of master computer>:11311"`
* `~$ export ROS_IP="<ip of slave device>"`

# Using rosserial
To run serial devices, we can use the `rosserial_python` package. `rosserial` is not downloaded by default. To install rosserial, we go to the ROS official wiki and find the link to the github page for rosserial.

Do a git clone to `~/catkin_ws/src`, then run `catkin_make`. This builds the packages. Now, technically you are supposed to be able to use `rosserial` after this, but I was faced with another issue. I had permission errors while trying to access the serial ports on my device.

This was my error:
```
[INFO] [1535809359.123765]: ROS Serial Python Node
[INFO] [1535809359.166418]: Connecting to /dev/ttyUSB0 at 57600 baud
[ERROR] [1535809359.174796]: Error opening serial: [Errno 13] could not open port /dev/ttyUSB0: [Errno 13] Permission denied: '/dev/ttyUSB0'
[ERROR] [1535809362.179596]: Error opening serial: [Errno 13] could not open port /dev/ttyUSB0: [Errno 13] Permission denied: '/dev/ttyUSB0'

```

To solve this, I did a bit of googling and found that i needed to give my username permissions to access the serial port. This was done by adding my username to the dialout group. `sudo usermod -a -G dialout $USER`. ($USER is an environmental variable, just type it as is)

After which, you have to re-login to enable this permission change.

Usermod is a command used to change attributes of existing users via command line. The dialout group allows you to access serial ports by reading and writing to the files in `/dev/tty*`. If you like, you can list all the devices in the `dialout` group by running `find /dev -group dialout`.


Discussion about groups can be found [here](https://askubuntu.com/questions/26179/what-do-the-groups-do-in-users-and-groups)
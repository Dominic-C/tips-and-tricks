# Using ROS across multiple devices
To use ROS across multiple computers, you have to select a device to act as a master, and the rest to act as slaves.

## Set up ROS master computer
This device will be running roscore. On this device, do the following:
* `~$ export ROS_MASTER_URI=http://<ip address of master computer>:11311`
* `~$ export ROS_IP=<ip address of master computer>`

## Set up ROS slave computer(s)
The device(s) will be subscribing to roscore from the Master device. Run the following:
* `~$ export ROS_MASTER_URI=https://<ip address of master computer>:11311`
* `~$ export ROS_IP=<ip of slave device>`

### Note:
For each shell instance, we need to run `export ROS_IP=...`, so it is advisable to create an alias for it in your .bashrc

You should be able to test this by running a tutlesim node and checking the rqt_graph on either device


# Building messages from source
The rough process for using source code found on github or other sources to build packages are as follows:

1. Download the packages desired.
2. Copy desired pacakges into `~/catkin_ws/src`
3. run `catkin_make install`

You might have to source your ROS setup files if you want to run the packages on your current terminal.

`source /opt/ros/kinetic/devel/setup.bash`

`source /catkin_ws/devel/setup.bash`

If you are running the subscriber on another machine, you might have to run `export ROS_MASTER_URI=..` and `export ROS_IP=..` again.


### Note:
For each shell instance, we need to run `export ROS_IP=...`, so it is advisable to create an alias for it in your .bashrc

You should be able to test this by running a tutlesim node and checking the rqt_graph on either device

Forgetting to put the inverted commas results in communication failure. This is because ROS variables must be in the form of strings.


# Building messages from source
The rough process for using source code found on github or other sources to build packages are as follows:

1. Download the packages desired.
2. Copy desired pacakges into `~/catkin_ws/src`
3. run `catkin_make install`

You might have to source your ROS setup files if you want to run the packages on your current terminal.

`source /opt/ros/kinetic/devel/setup.bash`

`source /catkin_ws/devel/setup.bash`

If you are running the subscriber on another machine, you might have to run `export ROS_MASTER_URI=..` and `export ROS_IP=..` again.

# Errors

## Catkin not installed
When trying to run `catkin_make`, I was thrown an error that went something like "catkin is not installed, to install catkin, run sudo apt install catkin". But when I tried installing catkin, the system said i had broken packages or missing dependencies.

It turns out that this was caused by forgetting to source `/opt/ros/kinetic/setup.bash`.


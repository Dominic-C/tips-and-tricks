# Hardware monitoring

## CPU
To list out cpu related information, we can run two different commands.
The first command is `cat /proc/cpuinfo`. This lists the CPU information regarding every single core on the CPU.

The second command is `lscpu`. This lists out the general CPU information including number of cores, CPU model information, Clock speeds, etc. The output from my Desktop is as follows:

```
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    1
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 94
Model name:            Intel(R) Core(TM) i5-6600K CPU @ 3.50GHz
Stepping:              3
CPU MHz:               948.968
CPU max MHz:           3900.0000
CPU min MHz:           800.0000
BogoMIPS:              7008.00
...

```

### Stress Testing
To stress test your CPU, you can download `Stress`
```
$ sudo apt install stress
```
To run the stress test, we can run
```
$ stress -c <number of workers> # no timeout

OR

$ stress -c <number of workers> -t <seconds> # stop running after 20 seconds
```

TODO: insert cpu monitoring software instructions

## USB devices

To list out USB devices, we can run the following command `lsusb`. This tells us which USB devices are connected to which USB bus (like internal USB hubs).

Alternatively, we can run `ls /sys/bus/usb/devices`. However it is more difficult to interpret. To see where your device is connected, you can run the command before and after plugging in your device. You can then spot the differences between both print outs.

# SSH copy (scp) syntax
## Usage
On computer with file you wish to transfer

`scp <file> <target username>@<ip address>:/<location to save file>`

# Rsync
Copy file from your computer to target computer

`rsync -av <location of file> <target username>@<target IP address>:/<location to save file>`

# Dealing with "dpkg-lock" issues
This occurs when apt processes are running and something you are trying to run wants to use the same resources

To solve this, we have to kill running apt processes. To find the processes, we run:

`ps -A | grep apt`

This lists all processes, then pipes the result to `grep apt`.

Then, we can kill the processes by running:

`sudo kill -9 <process number>`

OR

`sudo kill -SIGKILL <process number>`

Longer article for this issue can be found [here](https://www.tecmint.com/fix-unable-to-lock-the-administration-directory-var-lib-dpkg-lock/)

# Using grep
`grep` is a pattern search tool in unix based Operating Systems. It recognizes and prints out lines with a user defined pattern in the terminal output.

`|` is the symbol for piping. This means to pass an output of the previous command into the next command.

Combining the two commands, we can use `grep` to search for various keywords.

For instance, if we do `lscpu`, we get the output of our CPU information.

**Output:**
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
CPU MHz:               800.024
CPU max MHz:           3900.0000
CPU min MHz:           800.0000
BogoMIPS:              7008.00
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              6144K
NUMA node0 CPU(s):     0-3
```

To find information relating to Clock speeds of our CPU, we can run the command `lscpu | grep MHz`.

**Output:**
```
CPU MHz:               800.024
CPU max MHz:           3900.0000
CPU min MHz:           800.0000

```
Notice how grep searches for and prints out all lines that contain "MHz"? This illustrates the basic principle of using `grep`

# Using cat
`cat` (short for concatenate) is a command create and view files in the terminal.

## View text files
`cat` can be used to view text files. For example, we can run `cat /etc/passwd` to show the contents in `/etc/passwd`

## Write text files
`cat` can also be used to create text files. For example, we can create a text file `test1` by running `cat >test1`. we type in our desired lines and write it by pressing <Ctrl+d>

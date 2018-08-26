# SSH copy (scp) syntax
## Usage
On computer with file you wish to transfer

`scp <file> <target username>@<ip address>:/<location to save file>`

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

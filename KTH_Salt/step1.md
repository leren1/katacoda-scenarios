# Installing Salt

### Requirements
* Windows 10
* WSL2 running Ubuntu
* Python 3
* Administrator rights
* Ports 4505 and 4506 free

For this tutorial, we will be only using one machine for the master and minion. The master needs to be installed on a server or VM while the minion can be installed on nearly any operating system. We'll be installing the master on WSL2 (Windows Subsystem for Linux) running Ubuntu 20.04 and the minion on Windows 10 on the same machine. It is possible to install the minion on the same machine as the master. The master binds on ports 4505 and 4506 and so they must be available.

## Installation and configuration
**Note: to make sure everything works properly, we will ensure that the commands have root access by using `sudo`.**

### Installing Salt master
On your Linux command line, first update your packages by

```sudo apt-get update```

Then install the salt master by using 

```sudo apt-get install salt-master```

Don't start the master yet! We will configure it in step 2.

### Installing Salt minion on Windows
**Note: follow these instruction if you will be installing the minion on Windows. Otherwise, jump to the next header for Linux**

For Windows installations, download the stable branches here for your system:

Python3 x86 (32bit): [Salt-Minion-3004.1-x86-Setup.exe](https://repo.saltproject.io/windows/Salt-Minion-3004.1-Py3-x86-Setup.exe)

Python3 AMD64 (64 bit): [Salt-Minion-3004.1-AMD64-Setup.exe](https://repo.saltproject.io/windows/Salt-Minion-3004.1-Py3-AMD64-Setup.exe)

Follow the instructions on the installer and change the install location if needed. 

When you arrive to the settings screen, the default Master IP will be `salt` and minion name `hostname`. Since we'll be working locally on one machine, we will set Master IP to `127.0.0.1` and minion name to `windowsminion`. Choose `Default Config`.

<img src="assets/minion_config.png"  />

If you were an admin configuring Salt for a large network, instead of changing the Master IP for every minion installed, you would ideally make it so `salt` would resolve to the IP of the Master. But since we are working locally and on one machine, it is simpler to change the minion setting instead.


### Installing Salt minion on Linux

Install the Salt minion package by 
```
sudo apt-get install salt-minion
```

And that's it. We will configure the minion on the next step.

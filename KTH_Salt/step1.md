# Installing Salt

### Requirements

If you will use the Katacoda terminal, then no further requirements are needed. If you want to install it on your own Linux machine, then you will need:
* Python 3
* Administrator rights
* Ports 4505 and 4506 free on 127.0.0.1

For this tutorial, we will be only using the Katacoda terminal. The master needs to be installed on a server or VM while the minion can be installed on nearly any operating system. We'll be installing the master and the minion on the same machine by using the terminal. The master binds on ports 4505 and 4506 and so they must be available if you are installing on your own machine.

## Installation
**Note: to make sure everything works properly, we will ensure that the commands have root access by using `sudo`.**

### Installing Salt Master
On the terminal, first updates the packages by using:
```
sudo apt-get update
```

Then install the salt master by using 
```
sudo apt-get install salt-master
```

Don't start the master just yet. We will configure it in step 2.


### Installing Salt Minion

Install the Salt Minion package by 
```
sudo apt-get install salt-minion
```

And that's it. We will configure the minion on the next step.

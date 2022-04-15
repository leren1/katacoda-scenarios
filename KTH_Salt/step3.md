# Key management
Communication between Master and Minions is AES encrypted and so we'll need to accept the keys from the Minion.

### Starting the services
Start the Master as a daemon, that means as a process that runs in the background.
```
sudo salt-master -d
```

Start the minion in Windows by opening Task Manager, clicking the services tab and finding `salt-minion' and then right clicking and clicking start. 

If you installed the minion on Linux, then start it similarly to the Master.
```
sudo salt-minion -d
```

## Accepting keys
On your Linux command line, list the keys.
```
sudo salt-key
```

The outcome should look like this:
```
Accepted Keys:
Denied Keys:
Unaccepted Keys:
alpha
Rejected Keys:
```

You can accept all keys by using:
```
sudo salt-key -A
```

List the keys again and it should look like this:
```
Accepted Keys:
alpha
Denied Keys:
Unaccepted Keys:
Rejected Keys:
```

Now the Minion's key shuld be accepted by the master. We can verify the connection by running the `test.version` command:
```
$ sudo alpha test.version
alpha:
    3004.1
```

And now the setup is complete! The next step will show the powerful potential of Salt by showing example commands and how to filter using Grains. 
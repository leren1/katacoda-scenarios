# Key management
Communication between Master and Minions is AES encrypted and so we'll need to accept the keys from the Minion.

### Starting the services
Start the Master as a daemon, that means as a process that runs in the background.
```
sudo salt-master -d
```

Start the minion, also as a daemon.
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

**Note: If there is no key listed under `unaccepted`, wait a few minutes for the connection to establish, then try listing the keys again.**

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

Now the Minion's key should be accepted by the master. We can verify the connection by running the `test.version` command:
```
$ sudo salt alpha test.version
alpha:
    2015.8.8
```

And now the setup is complete! The next steps will show the powerful potential of Salt by showing example commands, writing custom modules and how to filter using Grains. 
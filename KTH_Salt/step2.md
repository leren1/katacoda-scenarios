# Configuring the master and minion

Before running the master and minion, we will configure them. 
### Configuring Salt master
On your WSL command line, the configuration file for the master is located at `/etc/salt/master`. Thus, we can open it in nano by 
```
sudo nano /etc/salt/master
```

Recall that we set the master IP to `127.0.0.1`, so do that here. Uncomment the `interface` line and change it to `127.0.0.1` as such:

<img src="assets/master_config.png"  />

Don't forget to save.

### Configuring Salt minion

If you installed the minion on Windows and changed the IP and hostname, you don't need to configure the minion and you can skip to step 3!

If you installed the minion on the terminal, then we will need to configure it here. 

The config file for the minion is located at `/etc/salt/minion` and so is opened by 
```
sudo nano /etc/salt/minion
```

Change the `#master:` line to `master: 127.0.0.1`.

Then, scroll down a few pages to the `#id` line. This is what the minion name will show up as. You can name this to your liking. We will change it to `id: alpha`. 

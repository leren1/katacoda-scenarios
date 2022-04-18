# Writing custom modules
In step 4 we tested our minions with modules that are already built in Salt. But, you can also write your own custom modules.

 The Salt Master has a simple file server built into it for distributing files to Minions. Execution modules are Python modules and are placed in `_modules` directory, which means that the modules should be placed in `/srv/salt/_modules`. Let's start writing our own simple module. 

Change to the `/srv` directory, then create the `salt/` directory, enter it and then create `_modules` and enter it: 
```
cd /srv
mkdir salt
cd salt/
mkdir _modules
cd _modules
```

In `_modules` we will create our Python module using nano:
```
sudo nano my_module.py
```
You can create whatever module you like but feel free to copy paste the code below to try things out:
```
# -*- coding: utf-8 -*-

from __future__ import absolute_import

def double(*args, **kwargs):
    return args[0] * 2
```

We define the encoding in the "shebang" and the import is for compatibility between Python 2 and 3. 

Save the file. We now need to sync this file to the minion by running `saltutil.sync_modules`:
```
$ sudo salt alpha saltutil.sync_modules refresh=True
alpha:
    - modules.my_module
```

The fileserver should now have synced the modules between the Master and Minion. Let's test it out:
```
$ sudo salt alpha my_module.double 5
alpha:
    10
```
And it works!

This was just a simple example but being able to write customs modules is a very useful tool. Check out the [documentation on writing custom modules](https://docs.saltproject.io/en/latest/ref/modules/) and [how the fileserver works](https://docs.saltproject.io/en/latest/ref/file_server/index.html) if you are interested in writing further modules. 

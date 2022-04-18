# Commanding the Minions
Now that we have connected Master and Minion, it is time to use Salt as it was meant. We can manage and send commands using the many modules that Salt has.

### Testing
Salt has a [testing module](https://docs.saltproject.io/en/latest/ref/modules/all/salt.modules.test.html) that contains many fun tests, we can try to test the connection.

For example, `test.echo` returns the string sent: 

```
$ sudo salt alpha test.echo '0x5f3759df'
alpha:
    1597463007
```

We can also try the famous [Collatz conjecture](https://en.wikipedia.org/wiki/Collatz_conjecture):
```
$ sudo salt alpha test.collatz 30
alpha:
    |_
      - 30
      - 15.0
      - 46.0
      - 23.0
      - 70.0
      - 35.0
      - 106.0
      - 53.0
      - 160.0
      - 80.0
      - 40.0
      - 20.0
      - 10.0
      - 5.0
      - 16.0
      - 8.0
      - 4.0
      - 2.0
    - 0.0
```

## Targeting Minions
Until now we have always targeted the minion `alpha` by targeting it directly in the commands. But what if we have many more minions and we only want to send commands to some of them? It is possible to use regex or [globs](https://en.wikipedia.org/wiki/Glob_(programming) but that might not cover all situations, for example, when you want to command minions running Windows.

 That is where [Grains](https://docs.saltproject.io/en/latest/topics/targeting/index.html#targeting) come in.

Grains is an interface that allows minions to be targeted through a large variety of system properties. Using a grain is done by passing the -G, specifying a grain and a glob expression to match. For example:
```
sudo salt -G 'os:ubuntu' test.version
```
will return `2015.8.8` from all minions running Ubuntu. 

You can list all available grains by executing `grains.items`:
```
sudo salt '*' grains.items
```



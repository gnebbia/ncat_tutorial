
Ncat is a general-purpose command-line tool for reading, writing,
redirecting, and encrypting data across a network. It aims to be
the network Swiss Army knife, handling a wide variety of
security testing and administration tasks. Ncat is suitable for
interactive use or as a network-connected back end for other
tools.
One of the main advantages of ncat is that it is installed by
default on many `*NIX` systems.

Let's see some usage examples:

```sh
ncat 192.168.1.105 3333
# connects ncat in "connect mode, to the mentioned host and port
```

With the next command we will create a server
with the "-l" option which is equivalent to "--listen" option,
if we omit the host address netcat will build the server on all
the network interfaces, while if we omit the port number, it
will use the default port number which is 31337, remember that
only root users can bind to a port number lower than 1024.
By default ncat uses TCP, but it is possible to use UDP, with the
"-u" flag or "--udp" option. When using a TCP server, the server
will send the packets to all client, while if we use the UDP
option, we'll send data only to the first connected client,
since in UDP, there is no list of "connected" clients concept

```sh
ncat -l 192.168.1.105 3333
```

Let's see some variations on this:

```sh
ncat -l -u 192.168.1.105 3333
 # in this case we create a UDP
 # server
```

```sh
ncat -l -u -6 192.168.1.105 3333
 # in this case we create a UDP
 # IPv6 server
```

```sh
ncat -l -v 192.168.1.105 3333
 # in this case we create a server
 # in the "verbose" mode, through the "-v" flag
```

```sh
ncat -nlvp localhost 8080
 # in this case we create a server in
 # the "verbose" mode, through the "-v" flag, and with the "-n"
 # option to not resolve the hostnames via dns of the connected
 # clients IP
```


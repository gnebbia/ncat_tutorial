# Netcat as a Chat

We can set up, a one-on-one chat with a simple

```sh
host1$ ncat -l
host2$ ncat host1
```

but this is useful only for two clients, when, instead we want to
build a multi-user chat, it is useful to use the "--chat" option,
which lets us distinguish between users, and automatically
enables "brokering" so a server will execute:

```sh
host1$ ncat -l --chat
host2$ ncat host1
host3$ ncat host1
host4$ ncat host1
```

in this case, "host1" acts as a server, and the other are the
clients.


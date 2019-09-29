
To Keep simultaneous and multiple connections with TCP protocol
we can use:

```sh
ncat -lk -p 3333 --sh-exec "echo -e 'HTTP/1.1 200 OK\r\n'; cat hello.http"
 # in this case we are working as a persistent web
 # server, the "-k" stands for "keep open", and indeed it is even
 # available with "--keep-open"
```

If instead we want to use multiple connections with UDP, we can
do:

```sh
ncat -l 3333 --udp --sh-exec "cat ciao.txt"
 # in this case we
 # allow multiple connections with the UDP protocol
```


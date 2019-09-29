
Ncat can encrypt its traffic using SSL. In connect mode, simply
add the --ssl option. Here is the syntax for connecting to an
HTTPS server:

```sh
ncat -C --ssl <server> 443
 # act as a https client, or a generic
 # SSL connection to a server and port, anyway if we get "Ncat:
 # Input/output error." it means that the service on the specified
 # socket doesn't talk SSL
```

```sh
ncat -C --ssl-verify <server> 443
 # act as a https client, this
 # option is used to require verification of the certificate and
 # matching of the domain
```

```sh
 ncat -C --ssl-verify --ssl-trustfile <custom-certs.pem> <server> 443
 # if we want to verify a connection to a server whose
 # certificate isn't signed by one of the deafault certification
 # authorities, use the --ssl-trustfile to name a file containing
 # certificates you trust. The file must be in PEM format
```

  Running a command with --exec

```sh
ncat -l --exec "/bin/echo Hello." localhost 3333
 # this command builds an echo server, when an host is connected to this
 # server, the "Hello" string is printed
```

```sh
ncat -l --sh-exec "echo `pwd`" localhost 3333
 # this command as
 # the previous builds a server on which we print message, but it
 # executes from a "/bin/sh -c" shell, so that we don't have to
 # provide the full path to commands if the commands are in "PATH"
 # and have sell facilities as pipelines and environment variable
 # expansion. This server when connected to, sends back the name
 # of its working directory
```

```sh
ncat -C --output smtp-debug.log mail.example.com 25
 # this will
 # transcript all the output to a file when connecting to the
 # mentioned server and port
```

```sh
ncat -C --hex-dump ssh-hex.log scanme.nmap.org 22
 # this gives us
 # an hexadecimal log
```

an alternative could be sending a string to netcat, this can be
done with:

```sh
printf "HEAD / HTTP/1.0\r\n\r\n" | nc 10.1.1.2 80
```

or if we want to save everything to a file we do:

```sh
printf "HEAD / HTTP/1.0\r\n\r\n" |nc 10.1.1.2 80 > myfile.txt
```


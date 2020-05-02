# File Transfers

We can transfer files in various modes, let's see some case.

##  File Transfer 1: Receiver Listening

```sh
host2$ ncat -l > outputFile
host1$ ncat --send-only host2 < inputFile
```

##  File Transfer 2: Seder Listening

```sh
host1$ ncat -l --send-only < inputFile
host2$ ncat host1 > outputFile
```

We have to remember that the order of the commands, is important,
the listener must be started first, since if this doesn't happen
the client cannot connect to anything.

##  File Transfer 3: Sender Listening (with bare minimum nc)

```sh
hostreceiver$ nc -l 3333 > nome_del_nuovo_file_in_output
hostsender$ nc -N hostreceiver 3333 < nome_file_da_trasferire
```

##  File Transfer 4: Using an Intermediary (brokering example)

```sh
host3$ ncat -l --broker
host2$ ncat host3 > outputFile
host1$ ncat --send-only host3 < inputFile
```

## File Transfer:  Other Examples

```sh
host2$ ncat -l | tar xzv
host1$ tar czv <files> | ncat --send-only host2
```

```sh
host2$ ncat -l > host1-hda.image
host1$ ncat --send-only host2 < /dev/hda
```

```sh
host2$ ncat -l | bzip2 -d > host1-hda.image
host1$ cat /dev/hda | bzip2 | ncat --send-only host2
```


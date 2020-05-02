# Access Control

A listening Ncat may control which hosts connect to it with the
`--allow` and `--deny`, let's make some examples:

```sh
ncat -l --allow 192.168.0.125 localhost 3333
 # allows only the
 # specified host to connect
```

```sh
 ncat -l --allow trusted.example.com localhost 3333
```

```sh
ncat -l --deny 192.168.0.200
 # allows all the hosts except the
 # mentioned one
```

```sh
ncat -l --allow 192.168.0.0/24
 # allows all the hosts on a
 # specific subnet
```

```sh
ncat -l --allow 192.179.0.0-200
 # allows all the specified IPs
 # (in ncat we use the same notation used in NMAP)
```

we can even deny or allow hosts specified in a file with:

```sh
 ncat -l --allowfile trusted-hosts.txt
```

```sh
 ncat -l --denyfile external-hosts.txt
```

we can even simply limit the maximum number of accepted
connections with:

```sh
ncat -l --max-conns 5
 # we set the maximum number of accepted
 # connections to 5, the default is 100
```

Other useful options are:

* `--nodns`: tells ncat to not resolve IPs into domain names, so it will
    show only IPs
* `--send-only` and `--recv-only`: are options used to make a one-way
    communication, in order to be sure to not send anything to another
    IP or to not receive anything from an IP



```sh
ncat -C scanme.nmap.org 80
 # in this case we use ncat as a web
 # browser, since we request tcp data to the specified address on
 # the port 80, and we use "-C" to convert CLRF chacters to actual
 # newlines; we need to remember that we must press "Enter" twice
 # to send the request.
```

Let's see some examples of request:

* In the case of HTTP/1.0
```http
GET /fileName HTTP/1.0
```
* In the case of HTTP/1.1
```http
GET /fileName HTTP/1.1
Host: nomeHost
```
we have to remember that HTTP/1.1 supports virtual hosts, so
even need to specify to which we are connecting to

to be able to connect to HTTPS websites we can execute:

```sh
ncat -C --ssl www.google.it 443
 # mi connetto ad un webserver sulla porta 443
```


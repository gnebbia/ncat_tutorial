# Usage as a Web Server

```sh
ncat -l localhost 8080 < hello.http
 # in this case we create a
 # web server, on the port 8080, where "hello.http" is the file
 # serving the html page, in the format shown below:
 #  HTTP/1.0 200 OK
 #  <html>
 #  <body>
 #  <h1> CIAO </h1>
 #  </body>
 #  </html>
```

Basically we put the first mandatory string, used in the
packet, to let the browser understand this is a web page, and
then we can put whatever html code.


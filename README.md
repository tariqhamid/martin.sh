martin and wwwwoosh
===================

wwwoosh
-------

a simple HTTP / CGI server written in shell, using netcat for a socket

martin
------

a sinatra-like web application framework, written in shell, with a CGI interface.

define handlers like this:

```shell
get "/" index; index () {
    header "Content-Type" "text/html"
    cat <<EOT
<html>
  <head>
    <title>hello world</title>
  </head>
  <body>
    PATH_INFO=$PATH_INFO
  </body>
</html>
EOT
}

get "/redirect" redirect_handler; redirect_handler () {
    status 302
    header "Location" "https://github.com/tlrobinson/martin.sh/"
}

get "/DeanMartin.jpg" dean_handler; dean_handler () {
    header "Content-Type" "image/jpeg"
    cat "DeanMartin.jpg"
}
```

notes
-----

hopefully it's obvious, but these projects are for fun and not meant to be taken seriously. wwwoosh can only handle about 2 request per second (any additional fail completely), not to mention there's probably some pretty nasty security issues with it.

it is, however, a demonstration of the simplicity of HTTP, and the power of unix shells

# Fetch

> Send a web request but retry if something goes wrong—but don't try too many times.

## Summary

Things go wrong when you send web requests—don't give up and keep trying; unless you try many times and things are still broken; then you should give up.

## Getting started

Send a web request to your laptop, then start a web server, then make the web request.

1. Get the code.

   ```
   git clone git@github.com:mbigras/fetch.git
   cd fetch
   ```

1. Send a web request to your laptop.

   ```
   go run fetch.go http://localhost:8080/
   ```

1. Open a new terminal.

1. Start a web server.

   ```
   python3 -m http.server 8080
   ```

1. Notice that fetch.go succeeds.

   The output should like the following:

   ```
   $ go run fetch.go http://localhost:8080/
   2022/03/20 15:23:14 [DEBUG] GET http://localhost:8080/
   2022/03/20 15:23:14 [ERR] GET http://localhost:8080/ request failed: Get "http://localhost:8080/": dial tcp [::1]:8080: connect: connection refused
   2022/03/20 15:23:14 [DEBUG] GET http://localhost:8080/: retrying in 1s (4 left)
   2022/03/20 15:23:15 [ERR] GET http://localhost:8080/ request failed: Get "http://localhost:8080/": dial tcp [::1]:8080: connect: connection refused
   2022/03/20 15:23:15 [DEBUG] GET http://localhost:8080/: retrying in 2s (3 left)
   2022/03/20 15:23:17 [ERR] GET http://localhost:8080/ request failed: Get "http://localhost:8080/": dial tcp [::1]:8080: connect: connection refused
   2022/03/20 15:23:17 [DEBUG] GET http://localhost:8080/: retrying in 4s (2 left)
   2022/03/20 15:23:21 [ERR] GET http://localhost:8080/ request failed: Get "http://localhost:8080/": dial tcp [::1]:8080: connect: connection refused
   2022/03/20 15:23:21 [DEBUG] GET http://localhost:8080/: retrying in 8s (1 left)
   <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
   <html>
   <head>
   <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
   <title>Directory listing for /</title>
   </head>
   <body>
   <h1>Directory listing for /</h1>
   <hr>
   <ul>
   <li><a href=".git/">.git/</a></li>
   <li><a href=".gitignore">.gitignore</a></li>
   <li><a href="fetch">fetch</a></li>
   <li><a href="fetch.go">fetch.go</a></li>
   <li><a href="go.mod">go.mod</a></li>
   <li><a href="go.sum">go.sum</a></li>
   <li><a href="README.md">README.md</a></li>
   </ul>
   <hr>
   </body>
   </html>
   ```

## Resources

Check out the following sources for more details:

* https://github.com/adonovan/gopl.io/blob/master/ch1/fetch/main.go
* https://pkg.go.dev/github.com/hashicorp/go-retryablehttp

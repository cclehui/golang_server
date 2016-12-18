# TCPServer
Package tcp_server created to help build TCP servers faster.

### Install package

``` bash
> go get github.com/firstrow/tcp_server
```

### Usage:

NOTICE: `OnNewMessage` callback will receive new message only if it's ending with `\n`

``` go
package main

import "./tcp_server"

func main() {
	server := tcp_server.New("localhost:9999")

	server.OnNewClient(func(c *tcp_server.Client) {
		// new client connected
		// lets send some message
		c.Send("Hello")
	})
	server.OnNewMessage(func(c *tcp_server.Client, message string) {
		// new message received
	})
	server.OnClientConnectionClosed(func(c *tcp_server.Client, err error) {
		// connection with client lost
	})

	server.Listen()
}
```


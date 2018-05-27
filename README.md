# HTTP/1.1

## Overview

<p align="center">
  <img src="https://github.com/manju16832003/http/blob/master/http_layers.png" width="550"/>
</p>

## Components of HTTP-based systems

```
- Client: the user-agent [browser]
- The Web server
- Proxies
```

## Basic aspects of HTTP

- HTTP is simple - HTTP messages can be read and understood by humans, providing easier developer testing, and reduced complexity for new-comers
- HTTP is extensible 
	- HTTP headers made it easy to etend and experiment with. 
	- New functionality can even be introduced by a simple agreement between a client and a server about a new header's semantics
- HTTP is stateless, but not sessionless
	- Core of HTTP itself is stateless
	- HTTP cookies allow the use of stateful sessions. Using header extensibility, HTTP Cookies allow session creation on each HTTP request to share the same context, or the same state
- HTTP and connections
	- Connection is controlled at the transport layer
	- HTTP subsequently relies on the TCP standard.
	- Underlying TCP connection can be partially controlled using *Connection* header

## What can be controlled by HTTP
	- Cache
	- Relaxing the origin constraint - Only page from the *same origin* can access all the information
	- Authentication - Basic authentication either using WWW-Authenticate or specific session using HTTP cookies
	- Proxy and tunneling - Servers and/or clients located on intranets and hide their true IP address to others.
	- Sessions - Using HTTP cookies allow you to link requests with the state of the server

## HTTP flow
	- Open a TCP Connection
	- Send an HTTP message
	
		GET / HTTP/1.1
		Host: developer.mozilla.org
		Accept-Language: fr
	
	
	- Read the response sent by the server
	
		HTTP/1.1 200 OK
		Date: Sat, 09 Oct 2010 14:28:02 GMT
		Server: Apache
		Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
		ETag: "51142bc1-7449-479b075b2891b"
		Accept-Ranges: bytes
		Content-Length: 29769
		Content-Type: text/html

		<!DOCTYPE html... (here comes the 29769 bytes of the requested web page)
	
	- Close or reuse the connection for further requests

## HTTP Messages
	- Requets: Consits of the following elements
		- HTTP method, 
			- VERB like GET, POST
			- Noun like OPTIONS or HEAD
		- The path of the resource to fetch - GET /(path) HTTP/1.1
		- The version of the HTTP protocol.
		- Optional headers
		- Or a body, for some methods likes POST
	- Responses
		- The version of the HTTP protocol they follow
		- A status code
		- A status message
		- HTTP headers
		- Optionally, a body containing the fetched resource

## APIs based on HTTP
	- XMLHttpRequest
	- server-sent events https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events


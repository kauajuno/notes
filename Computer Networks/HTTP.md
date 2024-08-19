HTTP stands for Hypertext Transfer Protocol, and it is a [[Computer network protocols|computer network protocol]] on the [[Computer network application layer|application layer]] used mostly for client-server communication to exchange resources (documents, photos, videos, etc.), which is identified by a [[URI|URI]]. HTTP is stateless, i.e., the server doesn't keep data between two requests. Messages sent from the client to the server are called requests, and messages from the server to the client are called responses.

# HTTP components

## Client

Client is the machine which sends request to the server. It is always the first to send a message, as the [[#Server|server]] shall never send not requested information to a client. A client is, most of the time, represented by the web browser, but it might also be represented by other programs used to debug their applications.

## Server

A server is the entity which provides responses to requests made by [[#Client|clients]]. For abstraction reasons, sometimes the server is thought of as a single machine, but not only the server software can be hosted in many machines, multiple server software instances can run in the same machine.

## Proxy

Proxies are machines which stand in between the client and the server when they establish a connection and start to communicate. Some machines operate only at the transport, network or physical levels, while some others are able to operate at the application layers for reasons such as caching, filtering, load balancing, authenticating and logging. These are called **proxies**.

# HTTP characteristics

- Simplicity: HTTP messages are meant to be high level, so its easier for developers to test and for beginners to understand.
- Extensible: HTTP headers make the protocol easy to extend and experiment with, as new functionalities can be introduced by a simple agreement between a client and a server about new header's semantics.
- Stateless but not sessionless: even though there is no persistence between two requests, but HTTP cookies allow the use of stateful sessions.
- Connections: to ensure no data is lost, the transport protocol used must be reliable, making TCP the standard for HTTP. TCP ensures a connection is established before messages are exchanged.

// TODO: https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview

Long-Polling - HTTP Long-Polling-
WebSockets
SSE
Ajax Polling
Websockets vs SSE (Server Sent Events)
Why would you choose Server-Sent Events over WebSockets?
Advantages of SSE over Websockets:
Advantages of Websockets over SSE:
Ideal use cases of SSE:

Long-Polling, WebSockets, and Server-Sent Events are popular communication protocols between a client like a web browser and a web server.

HTTP Long-Polling-

The basic life cycle of an application using HTTP Long-Polling is as follows:

The client makes an initial request using regular HTTP and then waits for a response.

The server delays its response until an update is available or a timeout has occurred.

When an update is available, the server sends a full response to the client.

The client typically sends a new long-poll request, either immediately upon receiving a response or after a pause to allow an acceptable latency period.

latency - DNS + request time (how much time to get the response) india-> US (200ms)

Each Long-Poll request has a timeout. The client has to reconnect periodically after the connection is closed due to timeouts.

Server-Sent Events (SSE)-

Under SSEs the client establishes a persistent and long-term connection with the server. The server uses this connection to send data to a client. If the client wants to send data to the server, it would require the use of another technology/protocol to do so.

The client requests data from a server using regular HTTP.

The requested web page opens a connection to the server.

The server sends the data to the client whenever there’s new information available.

SSEs are best when we need real-time traffic from the server to the client or if the server is generating data in a loop and will be sending multiple events to the client.

SSE is better when we have unidirectional communication.

It relies on a long-lived HTTP connection, where updates are continuously sent to the client.

Ajax Polling-

Polling is a standard technique used by the vast majority of AJAX applications. The basic idea is that the client repeatedly polls (or requests) a server for data. The client makes a request and waits for the server to respond with data. If no data is available, an empty response is returned.

The client opens a connection and requests data from the server using regular HTTP.

The requested web page sends requests to the server at regular intervals (e.g., 0.5 seconds).

The server calculates the response and sends it back, just like regular HTTP traffic.

The client repeats the above three steps periodically to get updates from the server.

The problem with Polling is that the client has to keep asking the server for any new data. As a result, a lot of responses are empty, creating HTTP overhead.

long polling kind of rpc- stock updates

Websockets vs SSE (Server Sent Events) 

Both are capable of pushing data to browsers, however, they are not competing for technologies.

Websockets connections can both send data to the browser and receive data from the browser. A good example of an application that could use WebSockets is a chat application.

SSE connections can only push data to the browser. Online stock quotes or twitters updating timelines or feeds are good examples of an application that could benefit from SSE.

In practice since everything that can be done with SSE can also be done with Websockets, Websockets are getting a lot more attention and love, and many more browsers support Websockets than SSE.

However, it can be overkill for some types of applications, and the backend could be easier to implement with a protocol such as SSE.

Furthermore, SSE can be polyfilled into older browsers that do not support it natively using just JavaScript. Some implementations of SSE polyfills can be found on the Modernizr GitHub page.

SSE suffers from a limitation to the maximum number of open connections, which can be especially painful when opening various tabs as the limit is per browser and set to a very low number (6). The issue has been marked as "Won't fix" in Chrome and Firefox. This limit is per browser + domain, so that means that you can open 6 SSE connections across all of the tabs to www.example1.com and another 6 SSE connections to www.example2.com (thanks Phate).

Only WS can transmit both binary data and UTF-8, SSE is limited to UTF-8.

Some enterprise firewalls with packet inspection have trouble dealing with WebSockets (Sophos XG Firewall, WatchGuard, McAfee Web Gateway).

HTML5Rocks has some good information on SSE. From that page:

Why would you choose Server-Sent Events over WebSockets? 

One reason SSEs have been kept in the shadow is that later APIs like WebSockets provide a richer protocol to perform bi-directional, full-duplex communication. Having a two-way channel is more attractive for things like games, messaging apps, and for cases where you need near real-time updates in both directions. However, in some scenarios data doesn't need to be sent from the client. You simply need updates from some server action. A few examples would be friends' status updates, stock tickers, news feeds, or other automated data push mechanisms (e.g. updating a client-side Web SQL Database or IndexedDB object store). If you'll need to send data to a server, XMLHttpRequest is always a friend.

SSEs are sent over traditional HTTP. That means they do not require a special protocol or server implementation to get working. WebSockets on the other hand, require full-duplex connections and new Web Socket servers to handle the protocol. In addition, Server-Sent Events have a variety of features that WebSockets lack by design such as automatic reconnection, event IDs, and the ability to send arbitrary events.

Advantages of SSE over Websockets:

Transported over simple HTTP instead of a custom protocol

Can be poly-filled with javascript to "backport" SSE to browsers that do not support it yet.

Built-in support for re-connection and event-id

Simpler protocol

No trouble with corporate firewalls doing packet inspection

Advantages of Websockets over SSE:

Real-time, two-directional communication.

Native support in more browsers

Ideal use cases of SSE:

Stock ticker streaming

Twitter feed updating

Notifications to browser

SSE gotchas:

No binary support

Maximum open connections limit

When using angular with WebSockets for events and control is it better to communicate in plain text or objects?

develop a chat feature using a third-party service called Sendbird.

WebSocket provides Full duplex communication channels over a single TCP connection. It provides a persistent connection between a client and a server that both parties can use to start sending data at any time. The client establishes a WebSocket connection through a process known as the WebSocket handshake. If the process succeeds, then the server and client can exchange data in both directions at any time. The WebSocket protocol enables the communication between a client and a server with lower overheads, facilitating real-time data transfer from and to the server. This is made possible by providing a standardized way for the server to send content to the browser without being asked by the client and allowing for messages to be passed back and forth while keeping the connection open. In this way, a two-way (bi-directional) ongoing conversation can take place between a client and a server.

you can create real-time applications with that such as chat, collaborative document editing, stock trading applications etc. it defined two-way communication b/w clients and servers. it uses a completely different protocol. Socket.IO is a JavaScript library for real-time web applications.

web socket is also a great feature i.e introduced in html5. firstly try to understand this then try with any library and framework.

 websocket is a protocol WS

The WebSocket protocol allows for constant, bi-directional communication between the server and the client.

ws: or wss:: URI -analogous to http or https

 a common use case of WebSockets is to send stringified JSON data or even binary data, allowing you to structure your messages in the format convenient to you

 WebSocket is a framed and bidirectional protocol. On the contrary, to this, HTTP is a unidirectional protocol functioning above the TCP protocol.

 As WebSocket protocol is capable to support continual data transmission, it’s majorly used in real-time application development

WS offer a long-lived, bidirectional communication channel between client and server.

Once established, the channel is kept open, offering a very fast connection with low latency and overhead.
ws is a popular WebSockets library for Node.js.

How WebSockets differ from HTTP
HTTP is a very different protocol, and also a different way of communicate.

HTTP is a request/response protocol: the server returns some data when the client requests it.

With WebSockets:

the server can send a message to the client without the client explicitly requesting something
the client and the server can talk to each other simultaneously
very little data overhead needs to be exchanged to send messages. This means a low latency communication.
WebSockets are great for real-time and long-lived communications.

HTTP is great for occasional data exchange and interactions initiated by the client.

HTTP is much simpler to implement, while WebSockets require a bit more overhead.

used for real-time, bidirectional and event-based communication between the browser and the server. it used HTTP Long Polling.
disadvantage of using HTTP Long Polling is that it consumes a lot of server resources.

Advantages of using HTTPS-
HTTP stands for Hyper Text Transfer Protocol. HTTPS, stands for Hyper Text Transfer Protocol Secure. 
As the name suggests, HTTPS is more secure than HTTP.
When the web server and the client communicate, using HTTP, protocol, the messages that are exchanged over the internet are not encrypted. 
Any one can secretly listen and see the messages that are exchanged between the client and the web server. 
That's why, any sensitive information like passwords, financial transactions should never be done over HTTP protocol. 
Most of the banking applications use HTTPS protocol. 
Messages exchanged between the client and web server, using the HTTPS protocol are encrypted and are very secure. HTTP use port 80 and HTTPS use port 443. 

What is Secure Socket Layer and how is it different from HTTPS
HTTPS is HTTP (HyperText Transfer Protocol) plus SSL (Secure Socket Layer). 
SSL standing for Secure Sockets Layer (SSL) is a standard security technology for establishing an encrypted link between a web server and a browser, 
so that the data sent over the Internet can’t be read by others.
When a user requests a secure Web page, the server generates an encryption key for the user’s session and then encrypts the page’s data before sending a response. 
On the client side, the browser uses that same encryption key to decrypt the requested Web page and to encrypt new requests sent from that page. 
SSL uses server certificates for encryption and decryption.
An SSL certificate contains a public key and certificate issuer. 
Not only can clients use the certificate to communicate with a server, clients can verify that the certificate was cryptographically signed by an official Certificate Authority. 
For example, if your browser trusts the VeriSign Certificate Authority, and VeriSign signs my SSL certificate, your browser will inherently trust my SSL certificate.

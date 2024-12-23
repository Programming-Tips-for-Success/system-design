overview of the HTTP
Protocols
HTTP request
HTTP status codes

overview of the HTTP

In the HTTP 1.1 version, there are 3 TCP connections while in HTTP version 2 there is 1 TCP connection. TCP carries data to the web server. Browsers have a same-origin policy, meaning that HTTP request from a server to a different server is not possible. so we cannot use HTTP.

The process starts from the time you type a website's URL in the search bar to finishing loading on your screen. These are the steps that this search follows-

Get the IP address of the URL.

The browser checks the cache for a DNS record to get the corresponding IP address

First, it checks the browser cache

Second, the browser checks the OS cache.

Third, it checks the router cache.

Fourth, it checks the ISP cache.

Once the browser gets the IP address it opens a TCP connection and sends an HTTP request to the web server.

The web server will manage the request (it happens in multiple steps) and send the HTTP response to the client/browser.

The browser parses the HTML document and renders it.

HTTP headers are bits of meta-data which the browser attaches to your HTTP requests when it sends them to the server. Things like your IP address, the type of browser you are using and so on are added to your headers. We then create request options and add our headers as a property of those options. By default, these requests return observables.

We send the below details to the server-

Request line: command, HTTP version number, web page requested,

Request header: Includes browser in-house, date, host, connection, accept-encoding, user-agent, accept

Request body: contains information that was sent to the server

We are getting this response from the server-

Response status: HTTP version, status code, reason phase

Response header: optional info including the server being used, date, URL of webpage/location, content-type, cookie, cache-control, expires, P3P, pragma, content-encoding, x-connection, the transfer encoding

Response body: The website(in HTML)

For example, let us send a basic Authorization header. This is simply a header called Authorization with a value that is a username and password converted to base64, No need to worry too much about the specifics just understand that the built-in javascript function btoa converts a string to base64.

Protocols-

20 & 21: File Transfer Protocol (FTP)

22: Secure Shell (SSH)

23: Telnet remote login service

25: Simple Mail Transfer Protocol (SMTP)

53: Domain Name System (DNS) service

80: Hypertext Transfer Protocol (HTTP) - used in the World Wide Web

110: Post Office Protocol (POP3)

119: Network News Transfer Protocol(NNTP)

143: Internet Message Access Protocol(IMAP)

161: Simple Network Management Protocol(SNMP)

194: Internet Relay Chat (IRC)

443: HTTP Secure (HTTPS)

465: SMTP Secure (SMTPS)

HTTP request-

The client opens a connection and requests data from the server.

The server calculates the response.

The server sends the response back to the client on the opened request.

HTTP protocol supports the following methods to retrieve data such as get, post, put, delete etc.

HTTP status codes-

These codes are official responses given by website servers on the internet. It is a numeric form code in which the first digit represents the class of response and others represent the specific role.

These are the kinds of messages returned every time your browser interacts with the server. If you’re a website owner or developer understanding status codes is very important. There are more than 40 distinct server status codes. But regularly, you will see a few codes.

Every time you click on a link or type in a URL & press “Enter” your browser sends a request to a web server. The web server accepts and processes the request, and then sends back the requested resources along with an HTTP header. HTTP status codes are received by your browser in the HTTP header.

The status codes are divided into some categories:

1xx Informational

it indicates an informational message only means the request has been accepted and the process is continuing.

2xx Success

It indicates success of some kind. It means the response was successfully received, understood, and accepted.

200 OK

201 Created(Data is Added) Post API

204 No Content

3xx Redirection

it redirects the client to another URL. It means more action must be taken to complete the request.

304 Not Modified

4xx Client Error

It indicates an error on the client’s part. It means the request contains the wrong syntax or cannot be fulfilled.

400 Bad Request, Invalid URL, Your browser sent a request that this server could not understand.

401 Unauthorized

403 Forbidden, on any webpage, if the user didn’t have permissions

404 Not Found

405-Method Not allowed

409 Conflict

5xx Server Error

It indicates an error on the server’s part means the server failed to fulfil a valid request.

500 Internal Server Error

httpstatuses.com/

https://howhttps.works/

https://howdns.works/

https://computer.howstuffworks.com/internet/basics/internet.htm

https://http.cat/
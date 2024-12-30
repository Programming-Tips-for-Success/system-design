REST vs RPC
SOAP vs REST
grpc
Why would you use gRPC?
serverless API
Client-Server Decoupling
Cacheability
Uniform Interface
Layered System Architecture

These are several models of web services. As we know to save data to the database or write business logic we need to do so on the backend side we can achieve this by doing communication over the network. Generally, we create an API service to send/receive data.

Following are the advantages of each service-

REST (Representational State Transfer)

SOAP (Simple Object Access Protocol)

RPC (Remote Procedure Call)

REST  vs RPC

REST is best described to work with the resources, whereas RPC is more about the actions.

REST can use HTTP for all four CRUD (Create/Read/Update/Delete) operations. RPC is used to communicate across the different modules to serve user requests.

REST is noun-centric and RPC is verb-centric.

REST is stateless. This means that each request should contain all the information required to process it. This can also mean that REST APIs don’t need any server-side sessions. Server applications aren’t permitted to store any data related to the client request.

SOAP  vs REST 

SOAP does not require HTTP protocol while REST Working on HTTP protocol.

SOAP work on the XML while REST returns JSON.

Unlike SOAP, a REST API is not constrained to an XML format and can return multiple data formats depending on what is needed. The data formats supported by REST API include JSON, XML, and YAML.

grpc - A high-performance, open-source universal RPC-Remote Procedure Call Framework. It can efficiently connect services in and across data centres with pluggable support for load balancing, tracing, health checking and authentication.

The main usage scenarios:

Efficiently connecting polyglot services in microservices style architecture.

Connecting mobile devices, and browser clients to backend services.

Generating efficient client libraries.

Why would you use gRPC?

The main usage scenarios:

Low latency, highly scalable, distributed systems.

Developing mobile clients which are communicating to a cloud server.

Designing a new protocol that needs to be accurate, efficient and language independent.

Layered design to enable extension eg. authentication, load balancing, logging and monitoring etc

used in microservices

HTTP protocols

1.0 is still in use

gRPC is a replacement for HTTP

https://github.com/grpc

https://grpc.io/

serverless API

Serverless technologies enable developers to concentrate on what the application does without the hassle of managing where it runs and how it scales. The cloud provider manages infrastructure, simply upload the applications, and the provider handles the rest.

Client-Server Decoupling: In REST API design, Server and Client applications must be completely independent of each other. The only information available to the Client-side should be the URI of the requested resource. Similarly, a server application shouldn’t change the client application other than passing the requested data through HTTP.

Cacheability: Whenever possible, resources should be Cacheable on the Server or Client-side. Server responses should also contain information on whether caching is allowed for the delivered resource. You should aim for improving performance on the client side while increasing scalability on the server side.

Uniform Interface: All API requests for the same resource should look the same, irrespective of where the request comes from. The REST API should ensure that the same piece of data, like the email address or name of a user, belongs to only one Uniform Resource Identifier (URI). Resources shouldn’t be too huge but should contain every piece of information that the client may need.

Layered System Architecture: In REST APIs the responses and calls go through different layers. You shouldn’t assume that the Client and Server applications connect directly to each other. There may be various intermediaries involved in the communication loop. Therefore, REST APIs need to be designed such that neither the server nor the client can tell whether it communicates with an intermediary or an end application

XML vs YAML

XML is an eXtensible Markup Language while Yaml(Yet Another Markup Language) is a human-readable data-serialization language.

XML stands for Extensible Markup Language, which has a set of codes and rules that describe the format of a text in an XML document
Yaml has nested indentation as Python. You can use white spaces but tab characters are not allowed. It uses both .yml or .yaml file extensions.

The main purpose of yaml file is to serve as a configuration file in an application as it is recommended to write the configurations of an application in YAML instead of JSON or XML as it is more flexible with good readability. A lot of automation tools like Ansible use it as part of its configuration and creation of processes. It can also be used to track the changes inside source control.

XML is used to describe the data. It separates the data from the presentation. It can be used in developing the HTML applications since HTML is used to format the data and XML can be used to send or receive the data. It can also be used with the conjunction of JavaScript language to read the data.

There are different types of APIS that we create like
HTTP (request methods verbs-GET-POST-PUT-DELETE-patch-head-jsonp) and Interacting with the server
CRUD    HTTP Verb
Create    POST
Read    GET
Update    PUT
Delete    DELETE

SOAP and XML created an excellent solution for creating connected web applications. SOAP is a standard XML based protocol that communicated over HTTP.
The SOAP offered an excellent way of transferring the data between the applications

REST stands for Representational State Transfer. 
REST is an architectural pattern for creating an API that uses HTTP as its underlying communication method. This is a protocol for exchanging data over a distributed environment. The main idea behind REST is that we should treat our distributed services as a resource and we should be able to use simple HTTP protocols to perform various operations on that resource.

GET: This maps to the R(Retrieve) part of the CRUD operation. This will be used to retrieve the required data (representation of data) from the remote resource.
PUT: This maps to the U(Update) part of the CRUD operation. This protocol will update the current representation of the data on the remote server.
POST: This maps to the C(Create) part of the CRUD operation. This will create a new entry for the current data that is being sent to the server.
DELETE: This maps to the D(Delete) part of the CRUD operation. This will delete the specified data from the remote server. 

What is a Web Application?
A web application is an application that is accessed by users using a web browser. Examples of web browsers include 
1. Microsoft Internet Explorer
2. Google Chrome
3. Mozilla FireFox
4. Apple Safari
5. Netscape Navigator

What are the advantages of Web applications?
1. Web Applications just need to be installed only on the web server, where as desktop applications need to be installed on every computer, where you want to access them.
2. Maintenance, support and patches are easier to provide.
3. Only a browser is required on the client machine to access a web application.
4. Accessible from anywhere, provided there is internet.
5. Cross Platform 

Web server-
a web server, is a software, that is used to deliver web pages to clients using the Hypertext Transfer Protocol (HTTP). 
For example, IIS is a web server that can be used to run asp.net web applications.

iis-
IIS (Internet Information Server) is one of the most powerful web servers from Microsoft that is used to host your ASP.NET Web application. 
IIS has it's own ASP.NET Process Engine to handle the ASP.NET request

Authentication is the process of identifying users. Authorization is the process of granting access to those users based on identity. 
Together, authentication and authorization secures our Web application.

Authentication - Who is the User?
Authorization - What rights the user has? What resources the user can access?

Most of the public web sites, does not ask the user to enter any user name and password.
But still, we will be able to access the content of these web sites.

How Web applications work?
1. Web applications work on client/server architecture
2. On the client all you need is a browser, that can understand HTML
3. On the server side, the Web application runs under Microsoft Internet Information Services (IIS) 

When the client enters the URL of the web application in the browser, and submits the request. The web server which hosts the web application, receives the request. The request is then processed by the application. The application generates, the HTML and hands it over to the IIS (web server). Finally, IIS sends the generated HTML to the client, who made the initial request. The client browser will the interpret the HTML and displays the user interface. All this communication, happens over the internet using HTTP protocol. HTTP stands for Hyper Text Transfer Protocol. A protocol is a set of rules that govern how two or more items communicate.

JSONP is a method for sending JSON data without worrying about cross-domain issues. JSONP does not use the XMLHttpRequest object it uses the <script> tag instead of Object. JSONP is JSON with padding, i.e, you put a string at the beginning and a pair of parenthesis around it. As we know Browsers have a same-origin policy, meaning that HTTP request from a server to a different server is not possible, so we cannot use HTTP in that case. we used JSONP in that condition.

//JSON
{"name":"overflow","id":5}

//JSONP
func({"name":"overflow","id":5});

JSONP Request callback example angular 2.0+ :



JSON with padding?
JSON response
{ ?username?: ?aditi?, ?name?: ?Shaumik Daityari?}
The same response with a callback function specified as processData is as follows.
JSONP Response
processData({ ?username?: ?aditi?, ?name?: ?Shaumik Daityari?})
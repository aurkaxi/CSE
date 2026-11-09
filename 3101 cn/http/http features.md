1. connectionless protocol
   http is a connectionless protocol. http client initiates a request and waits for a response from the server. when the server receives the request, the server processes the request and sends back the response to the http client after which the client disconnects the connection. the connection between client and server exist only during the current request and response time only
2. media independent
   http protocol is a media independent as data can be sent as long as both the client and server know how to handle the data content. it is required for both the client and server to specify the content type in mime type header
3. stateless
   http is a stateless protocol as both the client and server know each other only during the current request. due to this nature of the protocol, both the client and server do not retain the information between various requests of the web pages.
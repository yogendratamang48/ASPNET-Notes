## Web Applications Basics
#### Introduction ####  
Web application is an application that can be accessed through web browser or a specialized user agent. a HTTP request is created for specific urls (call for action methods) that map to resources (text file, html file, audio, video etc.). The server renders and returns HTML pages to the client.  
##### HTTP Basics ####  
HTTP is Application Layer Protocol for communicating between distributed systems World Wide Web(WWW) is based on HTTP. It is foundation of any data exchange on the web and a client-server protocol. It Provides standardized way for computers to communicate with each other.HTTP specification specifies how client has to send request and how server should response, thus providing rule for communication
##### HTTP Features: #####  
* **Simple and Human Readable**
* **HTTP Media is independent**  
 Any type of resource can be sent as long as servers and clients know how to handle such resource.
 * **HTTP is stateless**  
 There is no link between two requests being successfully carried out in the same connection.

##### HTTP Transaction #####  
An HTTP Client opens a connection and sends a request to HTTP Server.
The server returns a response message (Response usually contains requested resources). After delivering Request, Server closes the connection. Hence HTTP is called stateless protocol. A round trip, client requesting and server responding is known as HTTP transaction.  
Client and Server communicate eachother by exchanging messages. Message sent by client is called Request, Message sent from the server is known as Response.
##### HTTP Methods #####
* GET : This method is used to retrieve information from given server using a give URI. Requests using GET should only retrieve data and should have no other effect on data.
* POST: This method is used to send data to the server. For example sending Student form data, uploading file etc.
* DELETE: This removes all current representations of a target resource given by a URI.
* PUT: This is used to replace (or Update) all current representations of the target resource with the uploaded content.
#### HTTP Status Codes ####
HTTP Status codes are responses from the server. They represent what happended with our request. For example if you try to retrieve a file from server and you get 404 Status code, it means that the file is not present on the server.  
Some status codes are:
* 1XX: Informational  
This means request was received and the process is running
* 2XX: Success  
This means the action was successfully received, understood and accepted.  
* 3XX: Redirection  
It means further action must be taken to in order to complete the request.
* 4XX: Client Error
It means the request contains incorrect syntax or can not be fulfilled.
* 5XX: Server Error  
It means the server can not fulfill an apparently valid request.

#### References: ###
1. https://msdn.microsoft.com/en-us/library/ee658099.aspx
1. https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview


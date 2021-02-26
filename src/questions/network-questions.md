---
title: Network Questions
layout: layouts/page.njk
permalink: /questions/network-questions/index.html
---

* Traditionally, why has it been better to serve site assets from multiple domains?
  - It's because browsers usually have limits on the number of concurrent downloads from a domain at a moment. So, serving assets from multiple domains can increase the concurrent level.

* Do your best to describe the process from the time you type in a website's URL to it finishing loading on your screen.
  1. You enter a URL into a web browser
  2. (After caches have been checked) The browser looks up the IP address for the domain name via DNS
  3. The browser opens a TCP connection and sends a HTTP request to the server
  4. The server sends back a HTTP response to the client/browser
  5. The browser begins parsing the HTML
  6. The browser sends requests for additional assets embedded in the HTML (images, css, javascript) and repeat steps 3 - 5
  7. Once the page is loaded, the browser sends further async requests as needed

* What are the differences between Long-Polling, Websockets and Server-Sent Events?
  - HTTP long-polling: opens an HTTP request and remains open until an update is received. Upon receiving an update, a new request is immediately opened awaiting the next update.
  - Websockets: allows for constant, bi-directional communication between the server and client.
    - A WebSocket is nothing but a persistent connectioon between the client and the server. This is a communications protocol providing full-duplex communication channels over a single TCP connection.
    - Both HTTP and WebSockets are located at the application layer from the OSI model and as such depend on TCP at layer 4.
    - Compatible with HTTP
  - Server-sent events: SSE relies on a long-lived HTTP connection, where updates are continuously sent to the client.

* Explain the following request and response headers:
  * Diff. between Expires, Date, Age and If-Modified-...
    - Expires headers: tell the browser whether they should request a specifc file from the server or whether they should grab it from the browser's cache
    - Date headers: The date and time that the message was sent
    - Age headers: conveys the sender's estimate of the amount of time since the response was generated at the origin server.
    - If-Modified headers: is used with a method to make it conditional. If the requested variant has not been modified since the time specified in this field, an entity will not be returned from the server, instead, of a 304 (not modified) response will be returned without any message-body.
  * Do Not Track
    - disable either its tracking or cross-site user tracking
  * Cache-Control
    - tells all caching mechanism from server to client whether they may cache this object. It is measured in seconds.
  * Transfer-Encoding
    - The form of encoding used to safely transfer the entity to the user. Currently defined methods are: chunked, compress, deflate, gzip, identity.
  * ETag
    - An identifier for a specific version of a resource
  * X-Frame-Options
    - can be used to indicate whether or not a browser should be allowed to render a page in a <frame>, <iframe> or <object>

* What are HTTP methods? List all HTTP methods that you know, and explain them.
  - GET: used to retrieve information from the given server using a given URI. Requests using GET should only retrive data and should have no other effect on the data.
  - POST: used to send data to the server, for example, customer information, file upload, etc.
  - PUT: replaces all current representations of the target resource with the uploaded content.
  - DELETE: Removes all current representations of the target resource given by a URI.
  - Others:
    - HEAD: Same as GET, but transfers the status line and header section only, basically without the response body.
    - OPTIONS: Describes the communication options for the target resource, meaning it should return data describing what other methods and operations the server supports at the given URL.
    - PATCH: similar to POST and PUT, but the difference is that you only apply partial modifications to the resource.
    - CONNECT: Establishes a tunnel to the server identified by a given URI.
    - TRACE: Performs a mesage loop-back test along the path to the target resource.

* What is domain pre-fetching and how does it help with performance?
  - DNS prefetching allows the browser to perform the DNS lookups for links on a page in the background while the user browses the current page. This minimizes latency as when the user clicks on a link with DNS prefetch enabled, they do not have to wait for the DNS lookup to take place as it already has.
  - DNS prefetch can be added to a specific URL by adding the `rel= tag` to the link attribute like so: `<link rel="dns-prefetch" href="https://www.keycdn.com">`
  - DNS prefetch has been adopted by most modern browsers

* What is a CDN and what is the benefit of using one?
  - A CDN is a highly-distributed platform of servers that helps minimize delays in loading web page content by reducing the physical distance between the server and the user.
  - Benefits:
    - Less load on your server
    - Content delivery is faster
    - Global Reach
    - Caching
    - Availability
    - Analytics

* What is TCP/IP?
  - Today most computers communicate with other computers through TCP/IP.
  - Transmission Control Protocol/Internet Protocol
  - For any given interaction between two computer systems, the two computers need to know, ahead of time, how they are expected to communicate. Computers do this through protocols, which is just an agreed-upon set of rules. It's clear that an agreed-upon standard was needed that permitted computers from all vendors to communicate with each other. And that standard is TCP/IP.
  - TCP and IP are two separate computer network protocols.
    - IP is the part that obtains the address to which data is sent.
    - TCP is responsible for data delivery once that IP address is found.
      - Think of it this way: The IP address is like the phone number assigned to your smartphone. TCP is all the technology that makes the phone ring, and that enables you to talk to someone on another phone.
  - TCP/IP breaks each message into `packets`, and those packets are then reassembled on the other end. In fact, each packet could take a different route to the other computer, if the first route is unavailable or congested.
  - TCP/IP divides the different communication tasks into `layers`. Each layer has a different function. Data goes through four individual layers before it is received on the other end. TCP/IP then goes through these layers in reverse order to reassemble the data and to present it to the recipient. The purpose of the layers is to keep things standardized.
  - The four layers of the TCP/IP model:
    1. Datalink Layer
      - The datalink layer is what handles the physical parts of sending and receiving data using the Ethernet cable, wireless network, network interface card, device driver in the computer, and so on.
    2. Internet Layer
      - The internet layer (also called the network layer) controls the movement of packets around the network
    3. Transport Layer
      - The transport layer is what provides a reliable data connection between two devices. It divides the data in packets, acknowledges the packets that it has received from from the other device, and makes sure that the other device acknowledges that packet it receives.
    4. Application Layer
      - The application layer is the group of applications that require network communication. This is what the user typically interacts with, such as email and messaging. Because the lower layers handle the details of communication, the applications don't need to concern themselves with this.

* What is a HTTP request/response? What are other types of protocols?
  - Hypertext Transfer Protocol is used to structure requests and responses over the internet. The transfer of resources happen using TCP, which manages the channels between your browser and the server. TCP is used to manage many types of internet connections in which one computer or device wants to send something to another. HTTP is the command language that the devices on both sides of the connection must follow in order to communicate.
  - There are many alternatives but HTTP is a good choice to use because:
    - it's well understood with tons of documentation
    - it's well supported on both the client and srever including support in JavaScript and Web browsers
    - most networks are well set up to handle HTTP
  - TCP contains information about what data has or has not yet been received, HTTP contains specific instructions on how to read and process this data once it arrives. TCP manages the data stream, and HTTP describes what the data in this stream contains.
  - When you type a URL into your web browser, you are sending an HTTP request to a web server. That server will then respond, again using the formatting of HTTP.

* HTTP vs HTTPS?
  - essentially the same, but HTTPS is still slightly different, more advanced and much more secure.
  - HTTPS (the `s` stands for `secure`) is an extension of HTTP. In HTTPS, the communication protocol is encrypted using Transport Layer Security in OSI model.
  - HTTP operates at the application layer whereas HTTPS operates at the Transport Layer

* What is URI?
  - Uniform Resource Identifier is an identifier of a specific resource. Like a page, book, or a document.
  - URL is a special type of identifier that also tells you how to access it, such as HTTPS, FTP, etc. like https://google.com
  - Ultimately, URL is a subset of URI that specifies where a resource exists and the mechanism for retrieving it, while URI is a superset of URL that identifies a resource

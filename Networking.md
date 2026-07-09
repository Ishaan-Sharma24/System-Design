#Internet:
A global system of interconnected netwroks 
# Access networks 
These physically connect end sytems to the first router on a path to other systems
## 3 types
- Home access networks: Enable connectivity within a residentails env, use cable internet or fibre optic
- Institutional network : ussed by businesses and institutions 
- Mobile networks: which enable our smartphones to connect to the internet, These are cellular technologies like 5G

# Network Core
Its is based on the principle of packet swtiching
When you send and email or something over the internet, It doesn't go as a single stream instead it is broken in multiple chunks called packets. Each packet contains the portion of the data along with the information about the source and destination these packets are then sent individually through the network, they take different routes but end up at the destination.
## Advantage :
- It allows network to handle multiple communications simultaneously making efficient use of the bandwidth 
- Also provides resilience, if one route is congested or failed, The packet can go through another route

## Forwarding and Routing
 ### Forwarding 
 Forwarding is the local action of moving an arriving packet from router input link to appropriate router output lin, It is controlled by a forwarding table 
 ### Routing
 It is the global process of determining the full paths packets takr from source to dest.
 - Routing algo computes the shortest and most efficient paths between any 2 points on the global (BGP - Border gateway protocol)

 ## Protocols
 They are standard rules that define message formats (Header, checksum, address etc) and ordering of message exchnages and expected responses
 - TCP : Ensures reliable order delivery of data between applications. It handles things like breaking data into packets, acknowleding recieved packets and retransmitting lost packets
 - UDP : Offers faster but less reliable data transfer
 - IP : Responsible for addressing and routing packets accross the internet 
 - HTTP ; Protocol that powers the www, defining how message sare formatted and tranmitted 
betweem browsers and servers. When you type a URL into your browser 
HTTP is application layer protocol where as TCP and UDP are Transport layered ones, HTTP is based on these two 


# HTTP
Hyper text transfer protocol, It is the format of message, like request has headers, body, methods, status codes. REST are set of rules that API needs to follow to be RESTful 
- HTTP1; has headers, status codes methods: post and head. Each req needed its own connection this means a lot of back and forth; wan't very efficient 
- HTTP 1.1 : introduced persisitent connections, connec stay open unless told to close. It also introduced pipelining; this lets clients send multiple request over one tcp connection ( but there is one issue if the first req gets delayed the further ones will be delayed too )
    * Another feature was chunk transfer encoding servers could send resp in small chunks without waiting for the whole respm to be ready 
    * Also borught caching and added ehader
- HTTP 2 : Introduced a binary framing layer; mssgs are divided into smaller units called frames and send over the TCP connection the binary framing layer handles all this. responses of different req can be mixed and send and are put together on the binary layer 
    * Server push : server can send extra resp along with the requested one 
    * Header compression: uses HPACK to make heasers smaller 
    * multiple mssgs streams over a single connection
    Issue with HTTP2 was the TCP's way to handle the lost or delayed packets
- HTTP 3 : uses QUIC instead of TCP, it was build on UDP(connectionless protocol, doesnt need to connect before sending data), they handle packet loss better, improved multiplexing.
    * Handles netwrok changes well, if you switch from wifi to mobile data, they connection keeps going (Quakes connection ID, they dont depend on IP Addresses)
## Status codes in HTTP
200 : servers giving you a hifi  
201 : something new is created 
204 : No content, for ex somehting you wanted to delete that is successfull so 204 is returned with no content  

400 : a bad request, what is this check 
401 : unauthorized (Missing the right credential)
403 : Server is saying I know you but still I cannot provide you this specific information 

502- Issues between servers, proxy failing to get a response 
503 : Server can't handle the request now due to maintanance or traffic overload

300 Are the redirection codes 
301 : is a forwarding address, URL is pointing to a new End point 

101: Switching protocols when moving from HTTP to websocket 

# DNS 
Domain name system - It translates human readable domain names such as google.com to machine readable IP addresses


check more about Networking fundamentals:  
https://www.hellointerview.com/learn/system-design/core-concepts/networking-essentials
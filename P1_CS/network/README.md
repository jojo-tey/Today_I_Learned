# Network

- [Interview Questions for Network](#Interview-Questions-for-Network)
- [Comparison of HTTP's GET and POST](#Comparison-of-HTTP's-GET-and-POST)
- [TCP 3-way-handshake](#tcp-3-way-handshake)
- [Comparison of TCP and UDP](#Comparison-of-TCP-and-UDP)
- [HTTP and HTTPS](#http-and-https)
  - Problems with HTTP
- [DNS Round Robin](#dns-round-robin)
- [Flow of web communication](#Flow-of-web-communication)


[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Network)

</br>


* [Top 100 Networking Interview Questions & Answers from Career Guru](http://career.guru99.com/top-100-networking-interview-questions-answers/)

<br>


## Comparison of HTTP's GET and POST

Both are used to request something from the server using the HTTP protocol. However, the two characteristics should be well understood and used for the proper use for the purpose of the technology.

### GET

First of all, the GET method is that the requested data HTTP Request MessageIt is transmitted in url of the header part of . on the url for ? The data is attached to the back so that the request is sent. Because this approach is contained in a space called url, the amount of data that can be transferred is limited. And for data that needs to be secured, the data is exposed to url. GETThe method is not appropriate. (ex. password)

### POST

POST-style requests are: `HTTP Message의 Body` The data is sent in the part. Therefore, when requesting binary data, the size of the data is larger and better in terms of security than the GET method, as should be sent on POST basis (but from a security perspective, it is even as long as encryption is not done).

_Then, once you understand these characteristics, you need to find out where they apply so that you can clearly understand the difference._

First of all, GET is to bring. It is intended to bring some data from the server and show it without changing the value or status of the server. It can be seen as having a SELECT tendency. POST, on the other hand, is used to change or add to a server's value or state.

To look further at the incidental differences, GET-style requests can be cached in the browser. Therefore, if the GET-based request is made on the grounds that the size of the data that is sent is small and that there is no security problem, there is a possibility that the previously cached data will be answered. That is why we have to use technologies that fit our purpose.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Network)

</br>

## TCP 3-way Handshake

Attach a link instead because some pictures should be included.

#### Reference

- https://www.mdpi.com/2076-3417/6/11/358/htm

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Network)

</br>

## Comparison of TCP and UDP

### UDP

`UDP(User Datagram Protocol)`is a _disconnected protocol_. It provides a method of encapsulating and sending IP datagrams and sending them without setting up connections.

`UDP` does _not_ retransmit flow control, error control, or reception of damaged segments. All this is up to the user process. What `UDP` does is use ports to provide interfaces to IP protocols.

Often the client sends a short request to the server and expects a short response. If the request or response is lost, the client can time out and try again. Not only is the code simple, but it also requires fewer messages than the protocol required by the initial setup, such as TCP.

`DNS` is an example for `UDP` used. A program needs to find the IP address of any host name sends UDP packets including the host name to the DNS server. This server responds with UDP packets containing the host's IP address. No setup is required in advance and no release is required after that.
</br>

### TCP

Most Internet applications require _reliability_ and _sequential delivery_. UDP can't satisfy this, so it's created by the need for a different protocol. `TCP(Transmission Control Protocol)`is specifically designed to send _reliable byte streams_ end-to-end over unreliable Internet. TCP services are performed by creating endpoints that both senders and receivers call sockets. Connection establishment in TCP working through `3-way handshake`

All TCP connections are full-duplex, point-to-point. Full duplex means that transmission can occur simultaneously in both directions, and point-to-point means that each connection has exactly two termination points. TCP does not support multicasting or broadcasting.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Network)

</br>

## HTTP and HTTPS

### Problems with HTTP

- HTTP is a plain-text communication, so eavesdropping is possible.
- Because it does not check the communication partner, camouflage is possible.
- Modulation is possible because it cannot prove its completeness.

_The three above are common problems for other unencrypted protocols._

### TCP/IP is a tapable network.

Communication in the TCP/IP structure can be seen all over the communication path. You can eavesdrop just by collecting packets. When communicating by plaintext, it is necessary to communicate encrypted because it can understand the meaning of the message.

#### security method

1.  Encrypt communications themselves
    HTTP communication can be encrypted by combining different protocols(`SSL(Secure Socket Layer)` or `TLS(Transport Layer Security)`). HTTP with SSL call as `HTTPS(HTTP Secure)` or `HTTP over SSL`

2.  Encrypting only the contents
    Encrypt contents that are transported using HTTP. Once encrypted, the recipient needs to decrypt the password and print it out.

</br>

### Because it does not check the communication partner, camouflage is possible.

Anyone can send a request because communication by HTTP does not involve identifying who the opponent is. If there is no restriction on access to the web server, such as an IP address or port, anyone who receives a request will return a response of something. These features cause many problems.

1.  I can't verify that the web server from where the request was sent is the one that should send the originally intended response.
2.  It is not possible to confirm whether the client that returned the response was the client that originally sent the intended request.
3.  It is not possible to verify that the party with whom the communication is being communicated is the one who is permitted access.
4.  I can't see where and who made the request.
5.  It also receives meaningless requests. —> DoS attacks cannot be prevented.

#### Complementary method

You can check the other party with `SSL` mentioned in the above encryption method. SSL provides **certificate** as a means of verifying the other party. Since the certificate is issued by a trusted **third party**, it proves that the server or client exists. By using this certificate, the communication partner indicates that the server I want to communicate with, and the risk of leaking personal information to the user is reduced. One more advantage is that clients can use this certificate to verify their identity and use it for website authentication.

</br>

### Modulation is possible because completeness cannot be proved

Here, completeness means **the accuracy of information**. There is no guarantee that the content received from the server or client matches the content sent by the sender. After a request or response is sent, even if it is altered by someone while the other party is receiving it, this is not known. In this way, an attack in which an attacker steals and modulates a request or response in the middle is called a man-in-the-middle attack.

#### Complementary method

There are methods for checking hash values such as `MD5` and `SHA-1` and methods for verifying the digital signature of a file, but they cannot be verified for sure. You should definitely use `HTTPS` to prevent it. SSL provides authentication, encryption, and digest functions.

</br>

### HTTPS

> HTTP plus HTTPS with encryption, authentication, and integrity protection

`HTTPS` can be said to be HTTP over the SSL shell. In other words, HTTPS is not a new application layer protocol. It simply replaces the HTTP communication socket with a protocol called `SSL (Secure Socket Layer)` or `TLS (Transport Layer Security)`. HTTP originally communicated directly with TCP, but over HTTPS, HTTP communicates with SSL and **SSL communicates with TCP**. HTTPS using SSL enables encryption, authentication, and security protection.

In HTTPS SSL, a hybrid encryption system that combines the common key encryption method and the public key encryption method is used. After the common key is exchanged with the public key encryption method, subsequent communication is a method using the common key encryption.

#### Why not use HTTPS on all web pages

Compared to plain text communication, encrypted communication requires a lot of resources such as CPU and memory. Encrypting each communication consumes a lot of resources, reducing the number of requests that can be processed per server. Therefore, encrypted communication by HTTPS is used only when handling sensitive information.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Network)

</br>

## DNS round robin

### Problem of DNS Round Robin

1. Public IP addresses are required as many as the number of servers
   In order to increase the number of servers for load balancing, that much public IP is required.

2. Not evenly distributed
   This can be a problem in mobile sites, etc., but the connection of the smartphone is through a proxy server called a carrier gateway. In the proxy server, name conversion results are cached for a certain period of time, so connections through the same proxy server are always connected to the same server. Also, because the PC web browser also caches DNS query results, it is not evenly distributed over the load. It can be resolved to some extent by setting the TTL value of the DNS record short, but care must be taken since the cache is not released according to the TTL.

3. Unable to check even if the server is down
   The DNS server cannot control the query results depending on the load of the web server or the number of connections. It is not possible to detect whether the response is slow due to the high load of the web server or the connection cannot be processed because the number of connections is full. Because of this, users sometimes connect to a server that is down. DNS round robin is a method for load balancing only, not a multiplexing method, so it needs to be managed in combination with other S/W.

There is a DNS scheduling algorithm that solves the shortcomings based on the _Round Robin method. (Introduction only a part)_

#### Weighted round robin (WRR)

Each web server is weighted to change the distribution ratio. Of course, since servers with higher weights are selected more frequently, it is better to set higher weights for servers with higher processing power.

#### Least connection

Select the server with the fewest number of connected clients. It is necessary to manage the number of connections in real time in the load balancer or periodically notify each server.

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Network)

</br>

## Flow of web communication

_What happens when we run Chrome and enter a specific URL value in the address bar?_

### in browser

1. Investigate the meaning of the value entered in url according to the rule determined inside the browser.
2. Create an HTTP Request message according to the investigated meaning.
3. Send the created message to the web server.

The message is not sent directly by the browser. Since the browser does not have a function to send messages to the network, it requests the OS to deliver the message. When we send a courier, we do not send it directly, but it is the same reason as sending it using a courier system (courier company) that already has a service. However, when requesting transmission to the OS, the destination to receive the message must be designated by the IP address, not the domain name. In this process, the DNS server must be searched.

</br>

### in protocol stack, LAN adapter

1. The protocol stack (network control software built into the operating system) receives messages from the browser.
2. Save the message received from the browser in the packet.
3. Then, control information such as destination address is added.
4. Then, it passes the packet to the LAN adapter.
5. The LAN adapter converts the frame with the MAC address of the next hop into an electric signal.
6. Send the signal to the LAN cable.

When an error occurs during communication, the protocol stack plays a variety of roles, such as correcting it using this control information or controlling various situations. In the network world, there is a secretary, so when we hand over the item to the secretary, we write the recipient's address and other instructions! Here, it can be seen that the protocol stack acts as a secretary.

</br>

### in hubs, switches, routers

1. The frame transmitted by the LAN adapter arrives at the router for Internet access via the switching hub.
2. The router forwards the packet to the provider (communication company).
3. You enter the Internet.

</br>

### in access line, provider

1. Packets are carried to POP (Point Of Presence) by the access line (communication line) at the entrance of the Internet.
2. It enters the core of the Internet through POP.
3. Packets flow to the destination between numerous high-speed routers.

</br>

### in firewall, cache server

1. Packets pass through the core of the Internet and arrive at the LAN of the web server.
2. The waiting firewall inspects the arriving packets.
3. There is a cache server that determines whether packets should go to the web server or not.

Pick out cases where you don't have to go to the server. If the data of the accessed page is in the cache server, the value can be read without requesting the web server. Any data on the page that can be reused is stored in the cache server.

</br>

### in web server

1. When a packet arrives at the physical web server, the web server's protocol stack extracts the packet, restores the message, and passes it to the web server application.
2. The web server application that received the message puts the data according to the request message in the response message and sends it back to the client.
3. The response message is delivered to the client the way it came.

</br>

[Back](https://github.com/jojo-tey/Today_I_Learned) / [Top](#Network)

</br>

</br>

_Network.end_

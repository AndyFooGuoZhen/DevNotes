# Networking

Link : https://www.youtube.com/watch?v=5WfiTHiU4x8&t=983s

IP addresses

![image](https://github.com/AndyFooGuoZhen/DevNotes/assets/77149531/c19f2179-8145-4bde-8f9f-ba12ca19c902)

- Every device assigned an IP address by router
- Subnet mask tells us which portion of the IP address is fixed
    - EX : 255.255.255.0 tells us that the first three portions of the IP is fixed
    - 192.168.1 is always fixed, 0 tells us the device can have IP addresses between 0 - 255
    - Note that 0 and 255 is reserved, so devices can have 1 - 254
- Default gateway refers to the router
- When devices want to communicate with devices outside of local network, they use the router

OSI model

7 layers - All people seem to need data processing

![image](https://github.com/AndyFooGuoZhen/DevNotes/assets/77149531/3d6ebe75-98bb-467a-9235-9486427bb71b)

Application layer

- Google chrome, edge
- USes HTTP , HTTPS protocol
- FIle transfer (FTP) , email (SMTP) , web surfing (HTTPS)

Presentation layer

- Communicates with application and session layer
- Receives chars from application, perform translation to convert to bits, performs compression and encryption
- Protocols used in encryption (SSL)

Session layer

- Setup and manage connections
- Keeps track of files downloaded
- APIs
- When computer connects to server, authentication occurs
- After authenticated, authorization is allowed by server

Transport layer

- Performs segmentation
    - Segments data from session layer , each segment contains port and seq number
- Performs flow control
    - Control how much data is transferred between device and server
    - Device uses the TCP protocol to tells server what speed is adequate for communication
- Error control
    - If data packet is loss (known by performing a checksum), automatic repeat request will be performed
- Services
    - Connection oriented transmission (TCP)
        - Feedback needed
        - 
    - Connectionless (UDP)
        - Faster, no feedback
        - Streaming, games
    

Network layer

- Receives/send segments to and from transport layer
- Routing
    - Moving a packet from source to destination
- Logical addressing
    - IP addressing, Combines IP of sender and receiver to a segment to form a data packet
- Path determination
    - Choosing the best , shortest path to send

Data link layer

- Physical addressing
    - Combines mac address of receiver and sender to a data packet to form a frame

Physical layer

- Network cards, ethernet cables

Port forwarding

https://www.youtube.com/watch?v=2G1ueMDgwxw

- Networking technique to allow incoming network traffic to reach a specific computer on a private network
- EX : Using remote desktop, PC A can be used to control PC B
- PC A sends a public request with IP and Port 8000, Router At PC B location receives it, with port forwarding enabled, Router knows how to forward network Port 8000 to Designated Port 8000

---

## Communication protocols

API 

- Request response cycle (Two way communication)
- System A sends data to B , and B returns a response
- Stateless, can be scaled easy, request can be handles by other servers

WebHooks

- One way
- Sends data from One application to another when triggered by an event
- EX: Update deployment code base from gitlab to openshift

Polling

- Client keeps making request to server
- Lots of new connections created but lots of empty responses

Websockets

https://www.youtube.com/watch?v=xTR5OflgwgU

- Bi directional communication in real time
- After performing handshake between client and server application, a websocket session is created
- Typically used for real time applications, chatting stock trading
- Uses TCP connection
- Not stateless, handshake handled by one server only

---

## CDN (Content Delivery Network)

- Brings content closer to the user
- Servers at different locations in the world  (Edge Servers)
- Contents are cached in edge servers, if content not in edge servers, user will request it from origin server
- Edge servers Helps optimize content into more efficient forms

## DNS

- Domain name system
- Used as a “phonebook” for IP addresses
- User’s pc sends request to the DNS resolver
    - If DNS resolver has cached IP address it will return it
    - Else , it will reach to the root server
    - if root server doesnt have information about IP, it will provide information about TLD (top level domain’s server’s IP address)
    - TLD will have all information about IP
---
## Proxy

- Proxy is a server
- Middleman that sits between private network and public internet
- Forward proxy : Client forward request to proxy server, proxy server forward request to public internet (Protects client)
    - Regulates traffic by blocking harmful websites, blocking IP’s of client’s computer
- Reverse proxy : Client on internet wants to access data on private servers (Protects private server)
    - Clients on internet communicates with proxy , not private servers in direct
    - Client’s wont see IP of the private servers
---
## SSL

- Secure socket layer
- Encrypted link encrypted between web server and user’s browser
- Enables website to use HTTPS instead of http
- Certificates Authtirities verifies that website is legit

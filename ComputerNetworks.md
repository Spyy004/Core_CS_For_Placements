# Computer Networks

- Physical Layer and its functionalities
    
    Physical layer is the bottom most layer of any protocol. It is used to decide the type of topology, encoding, multiplexing, and mode of data transfer.
    
    Physical layer is the last layer which is seen by the sender and the first layer seen by the reciever. 
    
- Different types of topologies?
    
    Mesh Topology: It is a peer to peer topoplogy. Every node is connected to another node. It is secured, reliable and the cost is high because of a lot of wires and connectors required. It supports point to point connections
    
    Star Topology: Star Topology uses a single hub as a medium to transfer data to each other. So every node has just one connection, it is to the hub. It is not as secured as mesh because the data is being sent to the hub and anyone can access it.  It has a single point of failure hence it is not reliable
    
    Bus Topology:  Bus Topology is like a straight line with n number of ports. Each port has a node. Bus topology has a single point of failure and hence not much reliable. Bus topology is a multi point topology hence the number of collisions can be quite high.
    
    Ring Topology: Just turn the straight wire into a circle. It will be ring topology.  This topology also has a single point of failure and it is a multi point topology.
    
     
    
- What is DNS?
    - The domain name system (DNS) is a decentralized system that is used to resolve domain names (such as "**[www.google.com](http://www.google.com/)**") to IP addresses. It is an essential part of the internet, as it allows human-readable domain names to be translated into the numerical IP addresses that computers use to communicate with each other.
    - DNS consists of a hierarchical structure of DNS servers that are organized into a hierarchy. At the top of the hierarchy are the root DNS servers, which are responsible for storing information about the top-level domains (TLDs) such as ".com," ".net," and ".org." Below the root DNS servers are the top-level domain DNS servers, which store information about second-level domains (such as "google" in "**[www.google.com](http://www.google.com/)**").
    - When you enter a domain name into your web browser, the browser sends a request to the DNS to resolve the domain name to an IP address. The DNS server looks up the IP address associated with the domain name and sends it back to the browser, which then sends a request to that IP address to retrieve the content associated with the domain name. This process happens very quickly, so the user is usually unaware that it is occurring.
    - We don't hit the root server every time we search something. This is done only when we search for a website for the first time. From the next time, the ISP gives us the data since it has cached it.
- What is Class A IP Addressing
    - An IP Address is divided into 4 octets. Each octet is of 8 bit. The first octet is called as Network ID. The remaining 3 octets, each of size 8 are called as host ID.
    - In Class A IP Addressing, the first bit of the network ID is set to 0. Hence the range of Network ID goes from 0-127. Out of which the ID 0 and ID 127 are not given to any organization. So practically only 126 Network ID are usable.
    - Each network has 24 bits along with it for the host id. So in total there are 2^24 Hosts ID which are possible for a single network.
    - In every Octet, there are 8 bits and hence the value ranges from 0-255. The first host ID that is x.0.0.0 and the last host id that is x.255.255.255 is not given to any host
    - x.0.0.0 is used to identify the whole network whereas x.255.255.255 is  used to broadcast a message to every host in the network.
    - If from an IP address, we want to know the network of that IP address, we use a default mask. The Default mask of class A IP Addressing is 255.0.0.0
- What is Class B IP Addressing
    - In Class B IP Addressing, the network id takes two octets. The first two bits are set to be 10.
    - So there are 16 free bits and hence the total number of networks are 2^16.
    - The remaining 24 bits are used as hosts id. So for every network, there are 2^24 hosts.
    - Just like Class A, the first and last hosts ID are reserved for network identification and broadcasting.
    - The range of Class B's first octet is from 128-191.
    - The default mask for a Class B IP address is 255.255.0.0 . It is used to identify the network of the IP address.
- What is Class C IP Addressing?
    - The first three octets are reserved for networks in Class C. Out of which the first 3 bits in Octet 1 are set as 110. So the remaining 21 bits are variable. Which means there are 2^21 network ids.
    - The Class C's octet is from 192-223. Out of which the first one and last one are not use just like Class A and Class B.
    - The last octet is for the hosts. So the number of hosts in each network is 2^8.
    - The first two hosts of a network are not assigned to anyone because the first one is a network id and the last one is the broadcast id.
    - The Class C's default mask is 255.255.255.0. It is used to identify the network of an IP address.
- What is Subnet
    - Subnets are used to identify different smaller networks in  a large network of a particular organization.
    - A Class C subnet has a subnet mask of 255.255.255.0 but if the network has been divided into two parts then to identify the first subnetwork, the subnet mask will be 255.255.255.0
    - The second mask will be used to identify if the address belongs to second network or not. The second mask will be 255.255.255.255
- Ipv4 Header Format?
    - Ipv4 is internet protocol version 4 datagram
    - The number of IP addresses in Ipv4 is 2^28
    - A datagram consists of a header and a payload. The range of the header size in ipv4 is 20-60 bytes and range of payload is 0-65515 bytes. So the total size of the datagram is 2^16 bits
    - The datagram is divided into different parts. They are
    - Version 4 bits
    - HLen 4 bits
    - Types of Service(DSCP) 8 bits
    - Identification bits, Flag, and  Fragmentation offset  16,3,13 bits
    - TTL 8 bits
    - Protocol 8 bits
    - Header CheckSum 16 bits
    - Source IP and Destination IP 32 bytes, 32 bits
    - Options and Padding
- Ipv6 Header Format?
    
    Ipv6 Header Format is the latest header format.
    
    The number of ip addresses in Ipv6 is 2^128
    
    The size of base header in Ipv6 is 40 bytes. (320 bits)
    
    The whole header is divided into different parts. They are
    
    - Version 4 bits
    - Priority 8 bits
    - Flow Label 20 bits
    - Payload Length 16 bits
    - Next Reader  8 bits
    - Hop Limit 8 bits
    - Source Address 128 bits
    - Destination Address 128 bits
    - We can add different extension headers after the base header in ipv6 header format
- Differences between Ipv4 and Ipv6
    - In Ipv4, the address has 32 bit length and in Piv6, the address has 128 bit length
    - In Ipv4 end to end connection integrity is not possible and in ipv6 it is possible
    - Address representation in ipv4 is decimal and in ipv6 it is hexadecimal
    - In ipv4 checksumfield is available and in ipv6 it is not available
    - Ip4 header size varies from 20-60 bytes but it is fixed at 40 bytes in ipv6
    - In IPv4 Encryption and Authentication facility not provided. In IPv6 Encryption and Authentication are provided
- Different Types of Delays
    - There are 4 types of delays
    - Transmission Delay, Propogation Delay, Queuing Delay, Processing Delay.
    - Transmission Delay is the time taken for a packet to load from the source to the wire.
    - Propogation Delay is the time taken for the packet to go from one point to other
    - All the packets at the reciever end are stored in the queue. So the time taken by a process to come inside the queue and get out from it is called as Queuing delay.
    - The time taken by the reciever to process a data is called as processing delay.
- 3 Way Handshaking
    - 3 Way handshaking is a term used when a server and a client establishes a connection.
    - First, the client sends the server a header which consists of the source port, destination port,  a randomly generated sequence number, its buffer size, and the maximum size of a single message. It also sets the SYN flag to 1.
    - Then, when the server recieves this packet, it sends back a header which consists of server port no, client port no, a randomly generated sequence number and an acknowledge number, its buffer size, and maximum size of a single message. It sets the SYN and the ACK flag to 1.
    - Now, the client sends one last header with a sequence number, an acknowledge number and sets the ACK flag to 1.
    - So this way there are 3 different data exchange in order to establish a connection between server and client.
    - First we sync between client and server, then the server sync back plus acknowledges it, then finally the client acknowledges the acknowledgment recieved from server.
- What is HTTP
    - HTTP means hyper text transfer protocol.
    - It is a way to connect to the webpages.
    - HTTP's port number is 80
    - HTTP is an inbound protocol. Inbound means that it first sends command to the server to establish a connection before sending any messages.
    - HTTP is stateless. By stateless, it means that it does not store any data of the calls made. Companies use the concept of cookies to overcome this. With the help of cookies, the company/webpage can store important data which may be useful next time you visit the website.
- TCP vs UDP
    - TCP is connection oriented, UDP is connection less
    - TCP is more reliable and UDP is less reliable
    - Error control is mandatory in TCP, it is not mandatory in UDP
    - Transmission speed is slow in TCP whereas faster in UDP
    - Overhead size is more in TCP, less in UDP
    - There is flow control, congession control in TCP but no such features are available in UDP.
    - HTTP uses TCP. DNS uses UDP
- What happens when you enter www.google.com
    
    When you enter "**[www.google.com](http://www.google.com/)**" into your web browser, the following sequence of events occurs:
    
    1. Your browser sends a request to the domain name system (DNS) to resolve the domain name "**[www.google.com](http://www.google.com/)**" to an IP address. The DNS server looks up the IP address associated with the domain name and sends it back to your browser.
    2. Your browser sends a request to the IP address identified by the DNS server, using the hypertext transfer protocol (HTTP).
    3. The server at the specified IP address receives the request and sends back a response, which includes the HTML code for the Google homepage.
    4. Your browser receives the HTML code and renders the page, displaying the Google homepage on your screen.
    
    In summary, entering "**[www.google.com](http://www.google.com/)**" into your web browser initiates a series of events that involve your browser, the DNS, and a web server, resulting in the Google homepage being displayed on your screen.
    
- How do you handle unplanned outages?
    
    1. Identify the cause of the outage: The first step in handling an unplanned outage is to identify the root cause of the problem. This may involve reviewing log files, monitoring system metrics, or analyzing the environment in which the outage occurred.
    2. Communicate with stakeholders: It is important to keep stakeholders informed about the outage and the steps that are being taken to resolve it. This may involve sending updates via email, posting updates on a company website or social media, or using an incident management tool to coordinate the response.
    3. Develop a plan to restore service: Once the cause of the outage has been identified, it is important to develop a plan to restore service as quickly as possible. This may involve rolling back recent changes, deploying a fix, or restarting services.
    4. Implement the plan: The next step is to implement the plan to restore service. This may involve coordinating with a team of engineers or using automated tools to deploy changes.
    5. Monitor the system: After service has been restored, it is important to continue monitoring the system to ensure that it is stable and to identify any potential issues that may arise in the future.
    6. Review the outage: After the outage has been resolved, it is important to review the incident to identify any lessons that can be learned and to implement any necessary changes to prevent similar outages from occurring in the future.

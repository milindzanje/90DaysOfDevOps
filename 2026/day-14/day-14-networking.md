
#  OSI layer and TCP/IP expalanation 
Explian the OSI layer 

  # APPLICATION 
  HTTP , HTTPS, FTP, SMTP 
  # PRESENTATION
  ENCRYPTION & COMPRESSION
  # SESSION 
  SESSION MANANGEMENT 
  # TRANSPORT
  TCP AND UDP 
  # DATA LINK 
  ROUTING , IP
  # PHYSICAL
  CABLES AND SIGNALS 


  # TCP/IP MODEL 

  4 LAYERS 
  APPLICATION 
  PRESENATAION
  INTERNET 
  DATA LINK (NETWORK ACCESS LAYER)

# HOW data travels 

When you send a message, the data travels down through the layers (Application → Transport → Internet → Network Access), where each layer wraps the data in its own headers. Upon reaching the destination, the receiving device strips off these headers in reverse order (Network Access → Internet → Transport → Application) to read the original message.

# TCP vs UDP 

# TCP (Transmission Control Protocol)
TCP is built for accuracy. It verifies that every single piece of data successfully reaches its destination.
# How it works: Uses a three-way handshake (SYN, SYN-ACK, ACK) to establish a secure link. If a packet is dropped, TCP requests the sender to retransmit it.Best used for: Tasks where data corruption or loss is unacceptable.Examples: Web browsing (HTTP/HTTPS), sending emails, file transfers, and secure shell (SSH) logins.

UDP (User Datagram Protocol)UDP is built for raw speed. It is ideal for time-sensitive applications where a momentary glitch is better than a delay.How it works: Streams data directly to the recipient without handshakes or delivery verifications. Lost packets are simply ignored.Best used for: Real-time applications that prioritize instant delivery over 100% accuracy.Examples: Live video streaming (Twitch, YouTube), online gaming, Voice over IP (VoIP), and DNS lookups.

# imp commands
#1 . command to knoe the IP address of server 
hostname - i 
ip r l or ip addr show
command to know the public ip of server 
curl ifconfig.me

Reachability Test – Ping
# ping google.com
PING google.com (142.250.192.14) 56(84) bytes of data.
64 bytes from 142.250.192.14: icmp_seq=1 ttl=118 time=15.2 ms
64 bytes from 142.250.192.14: icmp_seq=2 ttl=118 time=14.8 ms
64 bytes from 142.250.192.14: icmp_seq=3 ttl=118 time=15.1 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss

# 2
traceroute google.com
1  192.168.1.1      1.2 ms
2  10.10.0.1        5.1 ms
3  172.16.5.10      8.2 ms
4  142.250.192.14   15.4 ms


* Number of hops
* High latency hops
* Timeouts


ss -tulpn or netstat -tulnp | grep 8080(port address)
verify whether the application is listening on the expected port using ss -tulpn

# DNS resolution 
use dig or nslookup to verify whether the hostname resolves to the correct IP address
dig google.com or nslookup google.com


# curl command 
curl -I https://google.com

o/p :
HTTP/2 200
content-type: text/html


curl -I http://localhost:8080

Output:

HTTP/1.1 200 OK

# netstat -an | head

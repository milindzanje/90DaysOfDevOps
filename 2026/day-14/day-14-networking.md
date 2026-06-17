
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

  

# DOS-attack-on-my-own-webserver

A Denial-of-Service (DoS) attack is a type of cyberattack where an attacker attempts to overload a computer or network, making it inaccessible to legitimate users. The goal is to disrupt the availability of a system or resource.

I want to observe a DOS attack, so I decided to make a simple webserver and attack it.

I've seen people in the internet doing this with two virtual machines on one machine, but I decided against it. Besides of the fact this person did not succeed, and I actually have a spare device to perform this, I thought it would make more sense to use two different devices, since in real life, attackers usually use a device/ devices appart from the server.

**1.SYN-Flood attack**
A SYN flood attack exploits a vulnerability in the TCP three-way handshake process, which is used to establish a connection between two computers.

Here's how a SYN flood attack works:

1. **Normal TCP connection:** In a normal TCP connection, a client sends a SYN packet to a server to initiate a connection. The server responds with a SYN-ACK packet. The client then sends an ACK packet to complete the connection.
2. **SYN flood attack:** In a SYN flood attack, the attacker sends a large number of SYN packets to a server, but never sends the corresponding ACK packets. This causes the server to maintain a half-open connection for each SYN packet it receives, consuming system resources.
3. **Server overload:** As the number of half-open connections grows, the server's resources become exhausted, and it is unable to handle new connection requests from legitimate users. This effectively denies service to legitimate users.

**Here are some of the effects of a SYN flood attack:**

* **Server crash:** The server may crash due to resource exhaustion.
* **Network congestion:** The network may become congested as the attacker's traffic overwhelms the network bandwidth.
* **Service disruption:** Legitimate users may be unable to access the server's services.


I will uses hping3 to send many SYN requests to the target device.

   a. Install hping3 on the attack device.
   b. turn on webserver on the target device.
      I used a simple python webs server: " python3 -m http.server "
      It will start a web server on port 8000.
   c. Turn on wireshark on the target device, in order to observe the network traffic.

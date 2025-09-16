# Networks

---

### **Layers of Network**

1. **Physical Layer**

   - **Function**: Transmits raw bitstreams over physical media (cables or wireless signals). Defines hardware aspects of networking.
   - **What is Formed**: Bits (binary data).
   - **Level**: Device-to-device (hardware interactions).
   - **Examples**: Ethernet cables, fiber optics, network interface cards.

2. **Data Link Layer**

   - **Function**: Provides error detection and correction, controls access to the physical medium, and packages bits into frames.
   - **What is Formed**: Frames.
   - **Level**: Node-to-node (direct communication between devices).
   - **Examples**: Ethernet (MAC addresses), Wi-Fi (MAC addresses), PPP.

3. **Network Layer**

   - **Function**: Handles routing of packets between devices across networks and manages logical addressing.
   - **What is Formed**: Packets.
   - **Level**: Device-to-device across networks (inter-network).
   - **Examples**: IP, ICMP, routers.

4. **Transport Layer**

   - **Function**: Ensures reliable end-to-end communication, error recovery, and flow control. Segments and reassembles data.
   - **What is Formed**: Segments (TCP) or Datagrams (UDP).
   - **Level**: End-to-end communication (between applications on different hosts).
   - **Examples**: TCP, UDP.

5. **Session Layer**

   - **Function**: Manages sessions between applications, including session establishment and termination.
   - **What is Formed**: Sessions.
   - **Level**: Application-to-application (dialogue management).
   - **Examples**: NetBIOS, RPC.

6. **Presentation Layer**

   - **Function**: Translates data for the application layer, handling encoding, encryption, and compression.
   - **What is Formed**: Data in a suitable format for the application layer.
   - **Level**: Application-to-application (data translation and transformation).
   - **Examples**: SSL/TLS encryption, ASCII/EBCDIC translation, compression (JPEG).

7. **Application Layer**
   - **Function**: Provides network services directly to end-user applications.
   - **What is Formed**: Application data exchanged between user applications.
   - **Level**: Application-to-application (services and data exchange).
   - **Examples**: HTTP, FTP, SMTP.

---

### **Additional Networking Concepts**

1. **TCP vs. UDP**

   - **TCP**: Reliable, connection-oriented protocol. Ensures data delivery and error recovery.
   - **UDP**: Unreliable, connectionless protocol. Faster but does not guarantee delivery.

2. **OSI and TCP/IP Models**

   - **OSI Model**: 7 layers (Physical, Data Link, Network, Transport, Session, Presentation, Application).
   - **TCP/IP Model**: 4 layers (Link, Internet, Transport, Application).

   | **Layer**        | **OSI Model** | **TCP/IP Model** |
   | ---------------- | ------------- | ---------------- |
   | **Application**  | Layer 7       | Layer 4          |
   | **Presentation** | Layer 6       | -                |
   | **Session**      | Layer 5       | -                |
   | **Transport**    | Layer 4       | Layer 3          |
   | **Network**      | Layer 3       | Layer 2          |
   | **Data Link**    | Layer 2       | Layer 1          |
   | **Physical**     | Layer 1       | -                |

3. **Error Control Algorithms**

   - **ARQ (Automatic Repeat reQuest)**: Ensures data integrity by requesting retransmissions in case of errors (e.g., Stop-and-Wait, Go-Back-N, Selective Repeat).

4. **Subnetting**

   - Dividing a larger network into smaller sub-networks to optimize performance and security. Involves determining subnet masks to create smaller networks.

5. **DNS, DHCP, NAT**

   - **DNS**: Resolves domain names to IP addresses.
   - **DHCP**: Assigns IP addresses dynamically to devices on a network.
   - **NAT**: Translates private IP addresses to public IP addresses for communication over the internet.

6. **SSL/TLS and Encryption Basics**

   - **SSL/TLS**: Protocols for securing data transmission over a network (encryption, authentication).
   - **Encryption**: Protects data confidentiality during transmission (e.g., AES, RSA).

7. **HTTP/HTTPS Protocols and Methods**

   - **HTTP**: Protocol for transferring hypertext (web pages) between client and server.
   - **HTTPS**: Secure version of HTTP, encrypts data using SSL/TLS.
   - **Methods**: GET (retrieve data), POST (send data), PUT (update data), DELETE (remove data).

8. **Firewall and Proxy Servers**
   - **Firewall**: Security system that monitors and controls incoming/outgoing network traffic.
   - **Proxy Server**: Acts as an intermediary between client and server, often used for security, anonymity, and caching.

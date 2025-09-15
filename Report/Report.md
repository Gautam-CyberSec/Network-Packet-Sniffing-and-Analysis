# Network Packet Sniffing and Analysis Report


## Objective

Capture and analyze network traffic to identify credentials, Suspicous activity. Demonstrate how insecure HTTP communications expose sensitive data and application vulnerabilities.

## Step-by-Step Process

### 1. Environment Setup
 • Started DVWA on localhost (http://localhost/DVWA).
 
 • Opened Wireshark and selected the lo (loopback) interface to capture localhost traffic.

 <img width="719" height="372" alt="Image" src="https://github.com/Gautam-CyberSec/Network-Packet-Sniffing-and-Analysis/blob/main/Screenshots/Screenshot%202025-09-15%20115105.png" />

### 2. Capturing Network Traffic
 • Started capturing packets in Wireshark before interacting with DVWA.
 
 • Performed various actions in DVWA.

### 3. Stopped and Saved Capture
 
 • Stopped the capture in Wireshark.
 
 • Saved the captured data as a .pcap file named: Wireshark.pcap

 <img width="719" height="372" alt="Image" src="https://github.com/Gautam-CyberSec/Network-Packet-Sniffing-and-Analysis/blob/main/Screenshots/Screenshot%202025-09-15%20115326.png" />

### 4. Analyzed the Capture

 • Applied filter: ip.addr == 127.0.0.1
 
→ Found multiple HTTP GET and POST requests between the client and server.

<img width="719" height="372" alt="Image" src="https://github.com/Gautam-CyberSec/Network-Packet-Sniffing-and-Analysis/blob/main/Screenshots/Screenshot%202025-09-15%20120411.png" />

 • Applied filter: http.request.method == POST
 
→ Found a POST request where login credentials were transmitted in plaintext.

<img width="719" height="372" alt="Image" src="https://github.com/Gautam-CyberSec/Network-Packet-Sniffing-and-Analysis/blob/main/Screenshots/Screenshot%202025-09-15%20120247.png" />
 
 • Further analysis of POST requests revealed an HTTP file upload operation.
 
 • Found that the uploaded file was named: revShell.php

 <img width="719" height="372" alt="Image" src="https://github.com/Gautam-CyberSec/Network-Packet-Sniffing-and-Analysis/blob/main/Screenshots/Screenshot%202025-09-15%20120307.png" />

 • Applied filter: http.request.method == GET

→ Found that a SQL injection attempt was tested by submitting malicious input in the URL.

<img width="719" height="372" alt="Image" src="https://github.com/Gautam-CyberSec/Network-Packet-Sniffing-and-Analysis/blob/main/Screenshots/Screenshot%202025-09-15%20120346.png" />

## Conclusion

This project demonstrated how insecure web applications transmit sensitive data such as login credentials and allow dangerous file uploads over HTTP.

 • All interactions were captured successfully.

 • Highlights the importance of HTTPS and strong input validation in web apps to prevent such vulnerabilities.

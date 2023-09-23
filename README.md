<h1>Network Traffic Analysis</h1>


<h2>Description</h2>
This project entails setting up Wireshark on an Ubuntu system, enabling non-administrator users who are part of the Wireshark group to conduct network packet capturing and analysis. The main objectives revolve around utilizing Wireshark for Ethernet packet capture, recognizing HTTP/S traffic, pinpointing IP addresses associated with visited web pages, and implementing IP address filtering within packet captures.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Linux</b>
- <b>Wireshark</b>
- <b>Firefox</b>

<h2>Environment Used </h2>

- <b>Oracle VirtualBox</b>
- <b>Ubuntu</b>

<h2>Project Overview:</h2>

Installed and set up Wireshark on Ubuntu: <br/>

- To get Wireshark on Ubuntu, I use the command: **sudo apt install wireshark**
- Wireshark should not be run as superuser for security reasons
- A user can be added to the Wireshark group to add packet capture capabilities by using the command: **sudo usermod -aG wireshark $USER**

<p align="center">
<img src="https://imgur.com/YwS4kMS.png" height="80%" width="80%" alt="Installation Steps"/>
<br />
<img src="https://imgur.com/PwWUhQb.png" height="80%" width="80%" alt="Installation Steps"/>
<br />
<img src="https://imgur.com/geP0kkD.png" height="80%" width="80%" alt="Installation Steps"/>
<br />
<br />
 
Started a packet capture on an ethernet port and saved it to a file: <br/>

- The wired interface includes the ethernet packet capture, which begins with ‘en’ in Wireshark
- The Wireshark app includes controls to start packet capture, stop capture, save the packets to a file, and load the capture file
- A capture can only be saved once the capture has stopped

<p align="center">
 

https://github.com/christopherandrade1/NetworkTrafficAnalysis/assets/145081683/13b0f795-baae-44bc-aeff-7715f8316566


https://github.com/christopherandrade1/NetworkTrafficAnalysis/assets/145081683/70c371e6-2c82-4768-bf3a-19ccd66a8aa0

<br />

Used a display filter to detect HTTPS packets:  <br/>

- Displayed only HTTPS traffic, using the filter: **tcp.port == 443**
 
<p align="center">


https://github.com/christopherandrade1/NetworkTrafficAnalysis/assets/145081683/814c7d95-b419-4b53-a20a-064c736912de

<br />

Visited a web page and detected its IP address using a display filter:  <br/>

- Utilized the TLS handshake display filter to detect a website visit in a packet list: **tls.handshake.type ==1**
- Utilized the IP address display filter to obtain packet information for a particular website: **ip.addr == 142.250.189.4**

<p align="center">



https://github.com/christopherandrade1/NetworkTrafficAnalysis/assets/145081683/12595c33-ff06-452c-88d0-6b5e0d7ed8a3


https://github.com/christopherandrade1/NetworkTrafficAnalysis/assets/145081683/5be8481e-8191-4b61-b433-49b52355671a

<br />
 
Located all HTTPS packets from a capture not containing a certain IP address:  <br/>

- Utilized a conditional statement to include all HTTPS alnog with the IP Address on a Wireshark capture: **ip.addr == 8.43.85.97 or tcp.port == 443**
- To avoid order of execution errors in a compound conditional statement I included parentheses: **!(ip.addr == 8.43.85.97) and (tcp.port == 80 or tcp.port == 443)**

<p align="center">


https://github.com/christopherandrade1/NetworkTrafficAnalysis/assets/145081683/dd415520-b1f0-4120-b674-e0419581e2b7


https://github.com/christopherandrade1/NetworkTrafficAnalysis/assets/145081683/f23b1dfc-9a71-40b3-9493-8fbca04e3b75



<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
- **Multimodal Encoding Stage.** Leveraging established encoders to encode inputs in various modalities, where these representations are projected into language-like representations comprehensible to the LLM through a projection layer.
```
--!>

<h1>Network Traffic Analysis</h1>


<h2>Description</h2>
This project involves the installation and configuration of Wireshark on an Ubuntu system to enable non-super users belonging to the Wireshark group to capture and analyze network packets. The primary focus is on using Wireshark to capture Ethernet packets, identify HTTPS traffic, detect IP addresses of visited web pages, and filter out specific IP addresses from packet captures.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Linux</b>
- <b>Wireshark</b>
- <b>Firefox</b>

<h2>Environment Used </h2>

- <b>Ubuntu</b>

<h2>Project Overview:</h2>

<p align="center">
Install and set up Wireshark on Ubuntu: <br/>

- To get the latest version of Wireshark on Ubuntu Linux, use the command: **sudo apt install wireshark**
- Wireshark should not be run as superuser for security reasons
- The user can be added to the Wireshark group to add packet capture capabilities: **sudo usermod -aG wireshark $USER**

<p align="center">
<img src="https://imgur.com/YwS4kMS.png" height="80%" width="80%" alt="Installation Steps"/>
<br />
<img src="https://imgur.com/PwWUhQb.png" height="80%" width="80%" alt="Installation Steps"/>
<br />
<img src="https://imgur.com/geP0kkD.png" height="80%" width="80%" alt="Installation Steps"/>
<br />
<br />
Start a packet capture on an ethernet port and save it to file: <br/>

- The wired interface includes the ethernet packet capture, which begins with ‘en’ in Wireshark
- The Wireshark app includes controls to start packet capture, stop capture, save the packets to a file, and load the capture file
- A capture can only be saved once the capture has stopped

<p align="center">
 

https://github.com/christopherandrade1/NetworkTrafficAnalysis/assets/145081683/13b0f795-baae-44bc-aeff-7715f8316566


https://github.com/christopherandrade1/NetworkTrafficAnalysis/assets/145081683/70c371e6-2c82-4768-bf3a-19ccd66a8aa0

<br />
<p align="center">
Use a display filter to detect HTTPS packets:  <br/>

- To display certain packets in an existing packet capture, use a display filter
- To display only HTTPS traffic, use a filter on TCP port 443: **tcp.port == 443**
 
<p align="center">


https://github.com/christopherandrade1/NetworkTrafficAnalysis/assets/145081683/814c7d95-b419-4b53-a20a-064c736912de

<br />

Visit a web page and detect its IP address using a display filter:  <br/>

- A TLS handshake display filter may be used to detect a website visit in a packet list: tls.handshake.type ==1
- The IP address is used in a filter to obtain packet information for a particular website: ip.addr == 142.251.163.105

<p align="center">
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Locate all HTTPS packets from a capture not containing a certain IP address:  <br/>

- A Conditional statement may be used to include and eliminate packets from a Wireshark capture: !(ip.addr == 8.43.85.97) and tcp.port == 443
- A compound conditional should include parentheses to avoid order of execution errors: !(ip.addr == 8.43.85.97) and (tcp.port == 80 or tcp.port == 443)

<p align="center">
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
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

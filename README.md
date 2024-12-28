<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 Pro (22H2)
- Ubuntu Server 22.04

<h2>High-Level Steps</h2>

- Create a Windows virtual machine and a Linux virtual machine
- Open Remote Desktop Connection on your PC (if using MAC, install Microsoft Remote Desktop)
  <img src="https://i.imgur.com/XfDNSei.png" height="90%" width="90%" alt=""/>

- Connect to the Windows virtual machine using its public IP address
<img src="https://i.imgur.com/in5a6K9.png" height="80%" width="80%" alt=""/>

- Once connected to the Windows VM, download and install Wireshark
  <img src="https://i.imgur.com/hCzQxcr.png" height="80%" width="80%" alt=""/>


<h2>Actions and Observations</h2>
<h3>Observing ICMP Traffic</h3>

- Open Wireshark on your Windows VM and start packet capture

<img src="https://i.imgur.com/hiAwWoZ.png" height="80%" width="80%" alt=""/>

<img src="https://i.imgur.com/TX9AK9M.png" height="80%" width="80%" alt=""/>

- Within Wireshark filter for ICMP traffic only
  
<img src="https://i.imgur.com/Q9fZ7q4.png" height="80%" width="80%" alt=""/>

- Retrieve the private IP address of the Linux VM and ping it from within the Windows VM
  
<img src="https://i.imgur.com/9QNqx3G.png" height="80%" width="80%" alt=""/>
  
  <img src="https://i.imgur.com/qvRnCVV.png" height="80%" width="80%" alt=""/>
  
- Observe ping requests and replies within Wireshark
<img src="https://i.imgur.com/rM4omYU.png" height="80%" width="80%" alt=""/>

- From the Windows VM open PowerShell or command line and ping a public website
- Observe the traffic in Wireshark 

<img src="https://i.imgur.com/sDDEDTr.png" height="80%" width="80%" alt=""/>





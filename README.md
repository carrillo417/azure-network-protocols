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
  <img src="https://i.imgur.com/PsuX1OT.png" height="80%" width="80%" alt=""/>


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

- From the Windows VM open PowerShell or command line and ping a public website. In this case, I used google.com
- Observe the traffic in Wireshark 

<img src="https://i.imgur.com/sDDEDTr.png" height="80%" width="80%" alt=""/>

<h3> Configuring a Firewall (Network Security Group) </h3>

- Initiate a perpetual/non-stop ping from your Windows VM to your Linux VM (Ex. <i>ping -t 10.0.0.0</i>)
- Open the Network Security Group your Linux VM is using and disable incoming (inbound) ICMP traffic
<img src="https://i.imgur.com/Oajm1uI.png" height="80%" width="80%" alt=""/>

- Since creating the new rule, no traffic should be coming in so now we get the message "Request timed out"
  
<img src="https://i.imgur.com/PhWcTZA.png" height="80%" width="80%" alt=""/>

- To change this back to normal, we can disable the rule or delete it

<img src="https://i.imgur.com/D0HPmhZ.png" height="80%" width="80%" alt=""/>


- It will take a while but after deleting the rule we are able to see the traffic again

<img src="https://i.imgur.com/cpPpdvo.png" height="80%" width="80%" alt=""/>

<h3>Observing SSH Traffic</h3>

- On Wireshark, still running on the Windows VM, start up a packet capture and filter for SSH traffic only
- From the Windows VM, login into the Linux VM using Powershell (ssh labuser@private IP address)
- Type in the Password and observe SSH traffic in Wireshark

<img src="https://i.imgur.com/bmbIxHO.png" height="80%" width="80%" alt=""/>

<img src="https://i.imgur.com/HcPPioK.png" height="80%" width="80%" alt=""/>

- Exit SSH connection by typing 'exit' and pressing Enter.

<h3> Observing DHCP Traffic </h3>

- Back in Wireshark filter for DHCP traffic only
- From your Windows VM, attempt to issue your VM a new IP address. Open PowerShell as admin and run: <i>ipconfig/renew</i>

<img src="https://i.imgur.com/pr2PS2a.png" height="80%" width="80%" alt=""/>

- Observe the DHCP traffic appearing in Wireshark
  
<img src="https://i.imgur.com/Ooc3Bdy.png" height="80%" width="80%" alt=""/>

<h3> Observing DNS traffic </h3>

- Back in Wireshark, filter for DNS traffic only
- From the Windows VM, open Powershell and us nslookup, if we look up google.com and disney.com, we are able to see what their IP addresses are. We are also able to see what goes on in the background in Wireshark

<img src="https://i.imgur.com/u1AFnHs.png" height="80%" width="80%" alt=""/>

<h3>Observing RDP Traffic</h3>

- Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)
- The traffic in Wireshark is non-stop due to the protocol constantly being used from one computer to another, so traffic is always being transmitted

<img src="https://i.imgur.com/uHhp6kf.png" height="80%" width="80%" alt=""/>








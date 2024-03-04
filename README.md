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

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create VM's in the same Network
- Download WireShark
- Block Traffic 
- Obesrve Traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://imgur.com/IZ2rPNm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Within your Windows 10 Virtual Machine, Install Wireshark
<br />

<p>
<img src="https://imgur.com/EdKt4z0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open Wireshark and filter for ICMP traffic only
</p>
<br />


<p>
<img src="https://imgur.com/4gMQioK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM
Observe ping requests and replies within WireShark

</p>
<br />


<p>
<img src="https://imgur.com/CmupAFJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark

<br />



<p>
<img src="https://imgur.com/SJmZAz9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
nitiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM

<br />



<p>
<img src="https://imgur.com/IQuq6AE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic

<br />


<p>
<img src="https://imgur.com/B6NpOgV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity

</p>
<br />


<p>
<img src="https://imgur.com/g04yJvK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
Stop the ping activity

</p>
<br />


<p>
<img src="https://imgur.com/GESPr9D.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in Wireshark, filter for SSH traffic only (Switched to Powershell)
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
Exit the SSH connection by typing ‘exit’ and pressing [Enter]

</p>
<br />


<p>
<img src="https://imgur.com/7Fie4Mk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
(Observe DHCP Traffic)
Back in Wireshark, filter for DHCP traffic only

<br />


<p>
<img src="https://imgur.com/eCd7cOD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
Observe the DHCP traffic appearing in WireShark

<br />


<p>
<img src="https://imgur.com/VJ0jrCf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Back in Wireshark, filter for DNS traffic only
From your Windows 10 VM within a command line, use nslookup to see what google.com 

<br />


<p>
<img src="https://imgur.com/ECZwIaA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Use nslookup to see disney.com’s IP address
Observe the DNS traffic being show in WireShark

<br />


<p>
<img src="https://imgur.com/cU02GzI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
(Observe RDP Traffic)
Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)
Observe the immediate non-stop spam of traffic

<br />

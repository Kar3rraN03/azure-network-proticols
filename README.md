# azure-network-proticols
# azure-compute-networking
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />



<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Deployment and Configuration Steps</h2>

  Part 1 (Create our Resources)

1. Create a Resource Group

2. Create a Windows 10 Virtual Machine (VM)
   
  a. While creating the VM, select the previously created Resource Group 
  
  b. While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet
  
3. Create a Linux (Ubuntu) VM
   
  a. While create the VM, select the previously created Resource Group and Vnet

4. Observe Your Virtual Network within Network Watcher

   Part 2 (Observe ICMP Traffic)

5. Use Remote Desktop to connect to your Windows 10 Virtual Machine
   
6. Within your Windows 10 Virtual Machine, Install Wireshark
   
7. Open Wireshark and filter for ICMP traffic only
   
8. Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM
   
 a. Observe ping requests and replies within WireShark
 
9. From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark
    
10. Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
    
 a. Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
 
 b. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
 
 c. Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using
 
 d. Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
 
 e. Stop the ping activity

Part 2 (Observe SSH Traffic)

11. Back in Wireshark, filter for SSH traffic only5

12. From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
    
 a. Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
 
 b. Exit the SSH connection by typing ‘exit’ and pressing [Enter]

Part 2 (Observe DHCP Traffic)

13. Back in Wireshark, filter for DHCP traffic only
    
14. From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
    
  a. Observe the DHCP traffic appearing in WireShark

Part 2 (Observe DNS Traffic)

15. Back in Wireshark, filter for DNS traffic only
    
16. From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are
    
     a. Observe the DNS traffic being show in WireShark

Part 2 (Observe RDP Traffic)

17. Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)
    
18. Observe the immediate non-stop spam of traffic

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/Qpd4JE0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Begin by creating a resource group in your cloud provider's console or through the command-line interface (CLI).
p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Proceed to create a Windows 10 VM within the selected resource group. During the creation process, ensure you allow the VM to create a new Virtual Network and Subnet, or select existing ones if applicable.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Similarly, create a Linux (Ubuntu) VM within the same resource group. Opt for the previously created Virtual Network and Subnet during this setup.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Utilize Network Watcher or a similar tool to observe the Virtual Network that has been created. This step ensures the network configuration is accurately set up.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Begin by connecting to the Windows 10 VM using Remote Desktop. Within the VM, install Wireshark and filter the traffic for ICMP packets.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Proceed to ping the Ubuntu VM from the Windows 10 VM, as well as ping a public website. Initiate a continuous ping from Windows 10 to the Ubuntu VM.
</p>
<br />


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, disable ICMP traffic in the Network Security Group (NSG) of the Ubuntu VM, and observe the changes in Wireshark and ping activity.
</p>
<br />


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Finally, re-enable ICMP traffic and observe any alterations.
</p>
<br />


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next SSH traffic, filter Wireshark for SSH traffic and SSH into the Ubuntu VM from the Windows 10 VM.
</p>
<br />


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
While connected, type commands and observe the SSH traffic in Wireshark. Exit the SSH connection once observations are complete.
</p>
<br />


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Moving on to DHCP Traffic. Filter Wireshark for DHCP traffic and attempt to renew the IP address of the Windows 10 VM using the ipconfig /renew command.
</p>
<br />


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Monitor Wireshark for DHCP traffic during this process.
</p>
<br />


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, DNS Traffic. Filter Wireshark for DNS traffic and use nslookup within the Windows 10 VM command line to query IP addresses for google.com and disney.com.
</p>
<br />


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observe the DNS traffic in Wireshark during these queries.
</p>
<br />


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Finally, RDP Traffic. Filter Wireshark for RDP traffic (tcp.port == 3389) and observe the traffic generated during an RDP session, if applicable.
</p>
<br />

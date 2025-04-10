<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we will observe various network traffic to and from Azure Virtual Machines usingreshark, and we will also experiment with Network Groups.. <br />


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

<h2>High-Level Steps</h2>

- Monitor ICMP Traffic
- Monitor SSH Traffic
- Monitor DHCP Traffic
- Monitor DNS Traffic
- Monitor RDP Traffic

<h2>Actions and Observations</h2>

 1.) The first step to create a resource group to house both of our virtual machines. After creating the resource group, proceed to create the first virtual machine, which will a Windows 10 VM. the resource group you created and name the virtual "VM1." Ensure you Windows 10 Pro, version 22H as the operating system. For the machine size, choose at least 2 vCPUs and16 GB of memory. Create a username and password of choice and retain default inbound port rules.

<p>
<img src="https://imgur.com/WgPD275.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  

<p>
<img src="https://imgur.com/X6ZMTJG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
2.) After this step proceed by "Next" until you reach the networking page, where a virtual network and subnet will be automatically created for us.  

<p>
<img src="https://imgur.com/XzdSPoR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Click review and create our VM.
  
  Now that we have created our first VM we will proceed to create our VM which will be an Ubuntu Server20.04 LTS machine. The process will be the same as creating our first machine, but this time we will switch from using an SSH public key to password 
  
<p>
<img src="https://imgur.com/0KT3Fmb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/pyxsHfF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Click next until we get to the networking page again.
  
  The network configuration should automatically provide us with the virtual network from1, including the subnet. 
  
<p>
<img src="https://imgur.com/3fQXRcw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 
 Click review and create, and it will create our second VM.
 
 2.) With both virtual machines operational, will connect to our Windows 10 using Remote Desktop Connection app. Once connected, we will open our browser to download and install Wireshark
 
 "Wireshark is a free and open-source packet analyzer. It is used for network troubleshooting, analysis, software and communications protocol development, and education." 
 
3.) Launch Wireshark and apply a filter to capture only ICMP traffic.
 
 <p>
<img src="https://imgur.com/RrtChUe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 
4.) Retrieve the private IP address of the Ubuntu VM and then attempt to ping it from the Windows 10 using Wireshark. To the private IP address the Ubuntu machine, open CMD orShell on the Windows and type: ping10.0.. the private IP address your Ubuntu machine.
 
<p>
<img src="https://imgur.com/zmJzyne.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 
<p>
<img src="https://imgur.com/pp4eZdK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 
 In either CMD or Powershell ping www.google.com and observe the traffic in wireshark.
 
5.) will then initiate a continuous from our Windows 10 VM to our Ubuntu.
 
6.) Access the Network Security Group for the Ubuntu machine and disable incominginbound) ICMP traffic. To achieve this, click "Add" to create a new rule and replicate all settings exactly shown in the provided. Once completed the rule will be created automatically and appear as a new rule.
 
 <p>
<img src="https://imgur.com/r3dH3Yy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 
<p>
<img src="https://imgur.com/qiSIrsX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 
Now that we have disabled incoming ICMP traffic from VM2, if return to VM1, you can that the ping request is out. 
 
7.) Re-enable IC traffic for the Security Group your Ubuntu VM is using.
In the Windows 10, observe the IC traffic in Wireshark and the command line ping activity ( start working).

 
 8.) The next step to observe SSH traffic

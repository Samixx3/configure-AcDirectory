<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines (VMs). By integrating on-premises Active Directory with Azure, you can enhance your organization’s security and manageability while leveraging the cloud’s flexibility..<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)


<h2>Deployment and Configuration Steps</h2>

<p>
</p>
<p>
In this lab, we will create two Virtual Machines (VMs) within the same Virtual Network (VNet) in Azure. One VM will serve as a Domain Controller (DC), while the other will function as a Client Machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/d22FHIm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this section, we will ensure that DC-1 has a static private IP address and that Client-1 can successfully connect to DC-1. Initially, we will encounter issues with pinging due to firewall settings, which we will resolve by enabling ICMPv4 on the DC-1 firewall.
</p>
<br />

<p>
<img src="https://i.imgur.com/HvZBWzc.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/1lrrGPw.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<p>
In this section, we will log back into DC-1 to install Active Directory Users and Computers, promote the VM to a Domain Controller, and set up a new forest with the domain name mydomain.com. After completing these steps, we will restart the VM and log in using the domain account mydomain.com\labuser.
</p>
<img src="https://i.imgur.com/cGjvRke.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>
Now that we have successfully set up Active Directory, we can proceed to create Organizational Units (OUs) to better organize our users and groups. In this step, we will create two OUs: _EMPLOYEES and _ADMINS. After that, we will create a user named Jane Doe and add her to the Domain Admins security group.
</p>
<img src="https://i.imgur.com/hL7g5Y5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>
<img src="https://i.imgur.com/kcgvzdE.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
Now that we have established Jane_admin as our administrator account, we can proceed to join Client-1 to the domain mydomain.com. This involves changing Client-1's DNS settings to point to the private IP address of DC-1 and then restarting the client machine. After you have successfully changed the DNS settings for Client-1 to point to the DC-1 private IP address and verified that Client-1 is using the Domain Controller for DNS resolution. This configuration is essential for joining the client machine to the domain, which we will do in the next steps.







</p>
<img src="https://i.imgur.com/jbrGTXW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>
<img src="https://i.imgur.com/kvcm2cY.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<p>
We have to join Client-1 to the domain in order to do so navigate to your system settings and go to about. Off to the right select rename this pc (advanced). From there select to change the domain. Enter "mydomain.com" after that enter your credentials from mydomain.com\labuser. Your computer will restart and then client-1 will be a part of mydomain.com
</p>
<br />
<p>
  <p>
<img src="https://i.imgur.com/Ze0Em5e.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Great to hear that Client-1 is now part of the domain! Next, we’ll set up Remote Desktop access for non-administrative users on Client-1.
</p>
<br />

<p>
  <p>
<img src="https://i.imgur.com/SApOKiE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To verify that normal users can Remote Desktop (RDP) into Client-1, we’ll use a PowerShell script to generate thousands of users in the domain.After the users are created we will select one and RDP into Client-1.
</p>
<br />
<img src="https://i.imgur.com/EzWG8ug.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
<p>
  <p>
<img src="https://i.imgur.com/Gkpe68K.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/n3gMwQV.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
<p>
As you can see the Powershell script created a user with the username "bab.hubo" We were able to login to Client-1 with his credentials as a normal user. 
</p>

<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1:
- Step 2:
- Step 3:
- Step 4:

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
"In this project, we will be using Azure to simulate the implementation of Active Directory onto a Windows Server VM, which can also be called the Domain Controller. The first step in this project is the creation of the Windows VMs. In Azure, create a Windows Server VM and a normal Windows 10 VM. Keep track of the username and password of both VMs in a note document. Also, make sure that for the Windows 10 VM, you select the same resource group and virtual network as the domain controller, because this lab wouldn't work without them being on the same virtual network.

<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, in Azure, go to the Domain Controller VM and click on the networking tab, then click on the network interface. Go to the IP config settings and click on the bar containing the private and public IP addresses. Then set the assignment to static. This makes the IP of the VM static. Open the Windows Server VM and install Active Directory by clicking 'Add Roles and Features' in the Server Manager. Make sure to click 'Active Directory Domain Services' during installation. After that, you will see a warning sign in the top right of the Server Manager on a flag. Click that icon, then click 'Promote this server to a domain controller.' The next tab asks you which deployment operation to select. Choose 'Add a new forest' and name the domain whatever you want. The format of the domain name should be (name.name), and it can be anything you want. Then create and write down the password for the domain and click 'Next' until the domain is created. The VM will log you out because it is resetting. To log back in, use the same credentials as the Windows Server VM, but in the context of the domain controller. For example, use 'name.name\labuser' with the same password.

<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open Active Directory and create a new Organizational Unit in the domain folder. Call it '_Employees.' Create a new user in the employee tab and name it whatever you want. Now, go back to Azure and set the DNS of the non-server VM to the IP address of the domain controller. To do that, find the private IP address of the Windows Server VM, copy it, then go to the other VM and find its virtual NIC. In the Virtual NIC settings, go to DNS servers and click 'Custom,' then paste the private IP address of the Domain Controller. Restart the Windows 10 VM.
</p>
<br />

<p>To check if the DNS settings worked, open the command line in Azure and type 'ipconfig /all.' After that, go to the settings of the VM: Settings > About > Rename this PC > Change the domain to the name of the domain controller (name.name) and log in to the domain admin account. Return to the same VM, and in settings, go to About > Remote Desktop > Select users who can remote access this PC > Add. In the empty box, type 'domain users' and click 'Check Names.' Now, all domain users are allowed to log into the normal Windows 10 computer. On the Windows Server side, all users can be seen in Active Directory in the Users tab. With that done, we have successfully used Azure to implement an on-premises Active Directory solution."</p>

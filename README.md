# active-directory-deploy

Project demonstration:  active directory deployment, client maintenance in Azure Virtual environment. 

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- Powershell / Powershell ISE
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows 10 Pro </b> (22H2) x64 Gen2
- Windows Server Datacenter 2022 - Azure Edition -x64 Gen2 



<h2>Installation Steps</h2>

<p>
  
![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/4b58ce4e-e37e-4e80-89fc-007a12d84c11)
</p>
<p>
I begin  with creating a domain controller virtual machine with Azure. The domain controller will be static instead of dynamic to ensure proper connectivity and maintain network reliability. Next, the client virtual machine is created using b both the Azure group name on the same virtual network as the domain controller. 
</p>
<br />
<p>

![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/622b3cd9-5e5d-40aa-8858-f8f2df8679b6)
<br />
![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/d960018a-837f-4607-96c0-af8e97e73958)
<br />



</p>
<p>
To ensure connectivity between both the client and domain controller, I log in to the client via  remote desktop and ping the domain controller's private IP address using the  ping -t command. While the ping's are in a  perpetual state, I log in to the domain controller to enable ICMPv4 on the local Windows Firewall - Core Networking Echo Request. Upon review, the initial ping is now successful. 
</p>

<br />

![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/a468eede-0457-4362-a5eb-ed01af464d61)

<p>
Continuing, I log in to the domain controller and install Active Directory Domain Services. 
</p>

<br /> 

![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/d96896fe-4135-465f-82fd-d1e7480ae3e6)

<p>
The domain is promoted and set up as a new forest and named "NEWDOMAIN" upon which I restart and log back into the domain under its new moniker. 
</p>





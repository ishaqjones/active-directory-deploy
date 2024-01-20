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
![image](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/4b58ce4e-e37e-4e80-89fc-007a12d84c11)



</p>
<p>
I begin  with creating a domain controller virtual machine with Azure. The domain controller will be static instead of dynamic to ensure proper connectivity and maintain network reliability. Next, the client virtual machine is created using b both the Azure group name on the same virtual network as the domain controller. 
</p>
<br />

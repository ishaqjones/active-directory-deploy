# active-directory-deployment

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

<br />

![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/afe9e915-db2e-4fce-a1d2-d5ba2f4cb0cd)

<p>
Next, I plan to create Admin and User Account in Active Directory beginning with the creation of an Organizational Unit, OU, 
called "_EMPLOYEES". 
</p>

<br />

![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/8a0ca0c8-3e8d-4488-a82a-44216f97e05e)

<p>
I follow up with an OU named "_ADMINS". I right-click the chosen domain and refresh for a sorted file listing. 
</p>

<br />

![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/7896effd-dda2-415a-b4f7-4b2fe2ac3494)

<p>
I create a new user by the name of Jane Doe and username of jane_admin for elevated privileges.  
</p>

<br />

![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/ee1dcbe4-0a27-4143-a67c-5259e7915cd4)

<p>
Continuing with elevated privileges, jane_admin has been added to the "Domain Admins Security Group.  
</p>

<br />

![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/694b7d06-8158-4121-9c4b-ead0bcdc79e3)

<p>
It is at this point that I log out of my primary credentials used to create the Azure VM and deployment of  Active Directory and log back in as the administrator Jane Doe. I open the command line and execute 'whoami' and 'hostname' to confirm- identification. I will use this account for further maintenance. 
</p>

<br />

![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/f5add615-0780-488a-bfd1-ada3216f7aab)



<p>
Before doing so, however, I will add the client workstation to the domain for centralized management. I achieve this from the Azure portal in the client's DNS settings and set them to the domain controllers' Private IP address. Upon restarting the client, logging in as the original local admin, and joining it to the new domain, the client computer will restart. 
</p>

<br /> 

![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/b2fd66fa-a253-4f85-b6f6-9f50ed00aaad)

<p>
For verification of the client in Active Directory I log in to the domain controller via remote desktop, ensuring its presence in the Active Directory Users and Computers  "Computers" container on the root of the domain. A "_CLIENTS container is created for continuity. 
</p>

<br />

![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/c2cae8e2-a10d-4c79-8cdf-2e101389e9ca)

<p>
To set up the Remote Desktop for non-administrative users on the client's computer, I log into the client as Admin Jane Doe, select "Remote Desktop", and allow "domain users" access to the remote desktop. This grants a non-administrative user normal usage.  Group Policy allows you to change many systems at once but I  thought this path was more explorative.
</p>

<br />

![alt text](https://github.com/ishaqjones/active-directory-deploy/assets/156931487/cea2fbb7-4743-432c-a62c-4651b805d351)


<p>
For further study, I located a name generator for Active Directory names for general login attempts and situational instances. The code for this portion was uploaded and implemented via Powershell ISE file. Upon execution, it generated a list of five thousand names. 
</p>





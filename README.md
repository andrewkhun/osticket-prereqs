<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- [Link to Downloads](https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)

<h2>Installation Steps</h2>

<br /><h2>Step 1 - Create an Azure Virtual Machine and Resource Group</h2>
<p>The first step is to create an Azure Virtual Machine and Resource Group. Navigate to the Azure Portal and create a Virtual Machine. Ensure you create a new Resource Group and name it accordingly.</p>
<p>
<img src="https://imgur.com/uRuN09F.png" height="70%" width="70%" alt="Create Azure Virtual Machine"/>
</p>
<p>
<img src="https://imgur.com/LiZ9WQp.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/DzckhoM.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Set up the virtual machine with Windows 10 Pro, version 22H2. For this particular deployment, we will specify 4 vCPUs and 16 GiB of RAM. Create your login credentials to access the virtual machine. Ensure the licensing box is checked off and that a virtual network has been created in the Networking Tab. After everything has been specified go to 'Review + Create' and create the virtual machine. 
</p>
<br />



<br /><h2>Step 2 - Remote Desktop to the Virtual Machine</h2>
<p>
Go to the newly created Virtual Machine in the Azure Portal locate the Public IP Address and copy it. On your local machine, open "Remote Desktop Connection" and input the copied IP address. Log in using the credentials set up during the VM creation.
</p>
<p>
<img src="https://imgur.com/Gysrja1.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/1uCVT0n.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/TXHprkA.png" height="35%" width="35%" alt="Resources"/>
</p>



<br /><h2>Step 3 - Install / Enable IIS in Windows with CGI and Common HTTP Features</h2>
<p>
Once inside the Virtual Machine, open up the control panel and select 'Programs'. From there, select 'Turn Windows Features on and off'. 
</p>
<p>
<img src="https://imgur.com/xmOrou5.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/t59Rt51.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
To install/enable IIS in Windows with CGI and Common HTTP Features, make sure the correct options are selected.

World Wide Web Services -> Application Development Features -> [X] CGI [X] Common HTTP Features

Internet Information Services -> Web Management Tools -> IIS Management Console
	[X] IIS Management Console
</p>
<p>
<img src="https://imgur.com/WK5LzCC.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/h83r69D.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
Once all the correct checkboxes have been selected, click ok to apply the changes. To confirm the changes have been properly applied, open the web browser and type '127.0.0.1' into the search bar and it should present the 'Internet Information Services' page displayed below.
</p>
<p>
<img src="https://imgur.com/XFqN4S9.png" height="70%" width="70%" alt="Resources"/>
</p>



<br /><h2>Step 4 - Download and Install PHP Manager for IIS, the Rewrite Module, and Microsoft Visual C++ Redistributable</h2>
<p>
From the <a href="https://drive.google.com/drive/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Link to Downloads</a>, download the files 'PHPManagerForIIS_V1.5.0.msi', 'rewrite_amd64_en-US.msi', and 'VC_redist.x86.exe'. After they have been downloaded, install all three onto the virtual machine.
</p>
<p>
<img src="https://imgur.com/ArPd1UX.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/Ir51bAt.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/wMW5Jmk.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/wO0tn61.png" height="35%" width="35%" alt="Resources"/>
</p>




<br /><h2>Step 5 - Download and Install PHP 7.3.8</h2>
<p>
Locate the 'php-7.3.8-nts-Win32-VC15-x86.zip' file and download it. 

!! ATTENTION !!
If this appears, choose to “Keep” the file:
</p>
<p>
<img src="https://imgur.com/B9yxJvO.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/AxzgeXG.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
Next head into the C:\ directory, create a folder, and name it 'PHP'. Unzip the contents of the 'php-7.3.8-nts-Win32-VC15-x86.zip' file into the new PHP directory C:\PHP.
</p>
<p>
<img src="https://imgur.com/QjLTS57.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/0JClFWb.png" height="70%" width="70%" alt="Resources"/>
</p>




<br /><h2>Step 6 - Download and Install MySQL5.5.62</h2>
<p>
Locate the 'mysql-5.5.62-win32.msi' file and download it. Once downloaded Run the setup wizard: Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration -> make the root password 'Password1' and finally select 'Execute' and 'Finish' once complete.
</p>
<p>
<img src="https://imgur.com/bonUtb3.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/jU3gHJJ.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/vDeMJak.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/hdNKUYg.png" height="35%" width="35%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/sz9tXMW.png" height="35%" width="35%" alt="Resources"/>
</p>


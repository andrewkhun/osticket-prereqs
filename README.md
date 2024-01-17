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


<br /><h2>Step 7 - Register PHP from within IIS</h2>
<p>
Now that we have the files downloaded and installed we will want to search for IIS in the Windows search bar. Open IIS as an administrator. Select the 'PHP Manager'
</p>
<p>
<img src="https://imgur.com/WP7tgMH.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Select 'Register new PHP Version'
</p>
<p>
<img src="https://imgur.com/BdvpC3A.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Provide a path to the php executable 'php-cgi.exe'. The file is located in our PHP directory 'C:\PHP'. After the file path has been selected, click 'OK'.
</p>
<p>
<img src="https://imgur.com/OfcKCDT.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Once done, restart the IIS server.
</p>
<p>
<img src="https://imgur.com/3yoQJba.png" height="70%" width="70%" alt="Resources"/>
</p>



<br /><h2>Step 8 - Download and install osTicket</h2>
<p>
Download the 'osTicket-v1.15.8' zip file. Once downloaded, extract the 'upload' folder within the zip file to the folder 'c:\inetpub\wwwroot'. Then rename the 'upload' folder to 'osTicket'.
</p>
<p>
<img src="https://imgur.com/OaICJQD.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/wNBcanU.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Once complete, go back into IIS and restart it once more. Navigate to sites -> Default -> osTicket, then on the right side of the IIS manager window, select 'Browse *:80'. This will open up your web browser and display the osTicket installer.
</p>
<p>
<img src="https://imgur.com/dWxMo7h.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/8PG5ABd.png" height="70%" width="70%" alt="Resources"/>
</p>




<br /><h2>Step 9 - Enable osTicket Extensions</h2>
<p>
To enable the necessary extensions, go back to the IIS manager, navigate to sites -> Default -> osTicket, then double click on 'PHP Manager'. Under 'PHP Extensions', click on 'Enable or disable an extension'.
</p>
<p>
<img src="https://imgur.com/5UDDMoK.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/dLDGji8.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Enable the following extensions:
	
- php_imap.dll
- php_intl.dll
- php_opcache.dll
</p>
<p>
<img src="https://imgur.com/aKDapBY.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Once done, refresh the osTicket installer and observe the changes. 
</p>


<br /><h2>Step 10 - Rename ost-config.php and Assign Permissions</h2>
<p>
Navigate to 'C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php'. Rename the 'ost-sampleconfig.php' to 'ost-config.php'.
</p>
<p>
<img src="https://imgur.com/FccMkNC.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Once the file has been renamed, right-click on 'ost-config.php' and go to 'Properties' then click 'Security', click on advance, and disable the inheritance to remove all inheritance permissions.
</p>
<p>
<img src="https://imgur.com/i8jKtdF.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Next click 'Add', then 'Select a principal'. In the textbox, type 'everyone' and ensure all permissions are checked. Click 'OK', then 'Apply' and 'OK' again.
</p>
<p>
<img src="https://imgur.com/c025Ek8.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/O1VmwRF.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/AKKetNf.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/XqNgnPA.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/8k31PH2.png" height="70%" width="70%" alt="Resources"/>
</p>


<br /><h2>Step 11 - Download and install HeidiSQL</h2>
<p>
Download and install HeidiSQL. Once you have completed the setup wizard for HeidiSQL, the program will open. Select 'New' on the bottom left. Make sure the username is root and the password is 'Password1' then click 'Open'.
</p>
<p>
<img src="https://imgur.com/z6e86F9.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/9wd9nQQ.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Once you have clicked open, a new instance of HeidiSQL will open. Right-click 'Unnamed' and select 'Create new', then 'Database'. Name the new database 'osTicket', then hit 'OK'.
</p>
<p>
<img src="https://imgur.com/21RPVtH.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/xegg4yM.png" height="35%" width="35%" alt="Resources"/>
</p>


<br /><h2>Step 12 - Finish osTicket Setup</h2>
<p>
Once you have completed the HeidiSQL setup, we can now go back to the osTicket webpage and click 'Continue'. Fill out the necessary fields under 'System Settings', 'Admin User', and 'Database Settings'.

 For this lab, the 'Helpdesk Name' is 'Lab Help Desk', and the default email is 'lab<span>@</span>helpdesk.com' 

 Under 'Admin User', input a 'First Name' (i.e. user), 'Last Name' (i.e. admin), 'Email Address' (i.e. user_admin<span>@</span>helpdesk.com), 'Username' (i.e. user_admin), and 'Password' (i.e. Password1). 

 Under 'Database Settings', make sure the 'MySQL Database' name is 'osTicket', the 'MySQL Username' is 'root', and the 'MySQL Password' is 'Password1'.

 Once all the fields have been filled out, click on 'Install Now'.
</p>
<p>
<img src="https://imgur.com/m7DFiwF.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Once complete, osTicket should be successfully installed! Congratulations!
</p>
<p>
<img src="https://imgur.com/FEE32n7.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
Notes:
Browse to your help desk login page: http://localhost/osTicket/scp/login.php  
End Users osTicket URL: http://localhost/osTicket/ 
</p>

<br /><h2>Step 13 - Clean Up</h2>
<p>The final step is to do some cleanup. Delete the folder 'C:\inetpub\wwwroot\osTicket\setup'. 
	
Then set 'Permissions' to "Read" and "Read and Execute" on C:\inetpub\wwwroot\osTicket\include\ost-config.php for 'Everyone':
- Right-click on 'ost-config.php', click on 'Properties', then the 'Security' tab.
- Click 'Advanced', then 'Edit' the permissions for 'Everyone'. Uncheck all the boxes except for 'Read & Execute' and 'Read', then click 'OK'.
</p>
<p>
<img src="https://imgur.com/i60h0qN.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
<img src="https://imgur.com/GNQiAkv.png" height="70%" width="70%" alt="Resources"/>
</p>
<p>
This concludes the prerequisite installations for osTicket!

To continue exploring osTicket and set up accounts and users, head over to [osTicket: Post-Installation Configuration](https://github.com/andrewkhun/post-install-config)
</p>

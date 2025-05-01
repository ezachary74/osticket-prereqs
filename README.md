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

- Microsoft Azure
- Remote Desktop
- Internet information services (IIS)
- My SQL
- osTicket

<h2>Installation Steps</h2>

![image](https://github.com/user-attachments/assets/9b0fa920-1957-477e-8850-3762783689e5)

![image](https://github.com/user-attachments/assets/fc705a2b-1783-4331-9bdc-9fa0506965f4)


Create a resource group in Microsoft Azure and name it osTicket. Following the resource group, create a VM in the Azure portal. Copy the VMs public IP address and paste it into the Remote Desktop.


![image](https://github.com/user-attachments/assets/32857deb-392b-420d-9b7c-a80a8e41312a)


Once connected to the VM, download the osTicket-Installation-Files.zip and unzip it onto the VM’s desktop. You will use the files in this folder to install osTicket.


![image](https://github.com/user-attachments/assets/e80401a2-8b9b-4a62-afd5-c4b7968da69e)


Install and enable IIS (Internet Information Services) in Windows with CGI. Navigate to the Control Panel through thw Windows icon and navigate to “Turn Windows Features On or Off”. Scroll down to locate IIS and check the box to activate it. Expand this selection, find World Wide Web Services/Application Development Features/CGI. Ensure that CGI is selected and then click OK.


![image](https://github.com/user-attachments/assets/8c302f88-9210-4a49-8f05-25cf0d5efd88)


From the “osTicket-Installation-Files” folder, install the PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi). Righ-click PHP Manager inside the file, select "install". Proceed by hitting "next", "I agree" to the terms, and finish installing.


![image](https://github.com/user-attachments/assets/85bde338-82d6-4d0b-9d25-a398b1fca788)


Install the Rewrite Module from the same file. Select "finish". 


![image](https://github.com/user-attachments/assets/da067dcf-6d81-4b57-a252-ddc58a282378)


Create the directory C:\PHP. From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder. Do this by right-clicking the file, select "extract all", in the browse bar select the PHP folder, and choose "Select Folder".


![image](https://github.com/user-attachments/assets/e6a2811b-eba4-4d02-aae0-463deed55283)


Navigate to the “osTicket-Installation-Files” folder, install VC_redist.x86.exe. Double click the file, select "install".


![image](https://github.com/user-attachments/assets/4affcf47-ccf1-4e81-bf3f-96a1b5dd391d)

![image](https://github.com/user-attachments/assets/15c7b8ec-ee03-4a64-8934-0306648e92ce)

![image](https://github.com/user-attachments/assets/198fc8da-5dcd-4a07-b92f-4156a5c7fc89)


Navigate to the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi). Launch the configuration wizard and choose standard configuration. For username and password, use “root” for both. We finalize the setup by clicking the execute button.

![image](https://github.com/user-attachments/assets/065287da-a87e-4354-a18b-785e610da67b)

![image](https://github.com/user-attachments/assets/983900a6-c844-4586-9dbb-e84594d5974d)

![image](https://github.com/user-attachments/assets/b7cfd6ef-0d43-45c6-9a64-0240a4efa325)


Open IIS as an Admin by navigating to the Windows icon, search for IIS, right-click IIS, and run as Admin. Register PHP within IIS. Restart the server by selecting “stop” and "start" in the IIS Manager.


![image](https://github.com/user-attachments/assets/72fef9a0-00b1-4c2a-9676-0fdaf0a7a6ed)


Install osTicket. Navigate to the osTicket-Installation-Files folder, we unzip osTicket-v1.15.8.zip and copy the upload folder to C:\inetpub\wwwroot. Then, within C:\inetpub\wwwroot, we rename the upload folder to osTicket.


![image](https://github.com/user-attachments/assets/3f1ae410-a1ae-4b88-b23a-e0595c635f88)

![image](https://github.com/user-attachments/assets/2940d238-1f2c-4235-a1e8-c44de7fd5f8b)


Reload the IIS server as you did previously. Navigate to Sites > Default > osTicket, and on the right, click “Browse *:80”. os
ticket should open. Enable the necessary PHP extensions by navigating to IIS again. Go to Sites > Default > osTicket > double-click PHP Manager. Select “Disable or enable an extension” and enable php_intl.dll, php_opcache.dll and php_imap.dll. Finally, refresh the osTicket web server and verify that the Intl Extension is now enabled.


![image](https://github.com/user-attachments/assets/ea18e0c1-55c0-4c2c-9714-03cbccb8d2e5)


 Navigate to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php and rename the file to ost-config.php in the same directory (C:\inetpub\wwwroot\osTicket\include).


![image](https://github.com/user-attachments/assets/c6cdbb02-8745-453f-9bce-38be8844fd3c)


 Assign Permissions to file "ost-config.php". Right-click the file and select “Properties”. In the Security tab select "Advanced", disable inheritance, remove all inherited permissions, and grant “everyone” full access. Check the "Full control" box.


 ![image](https://github.com/user-attachments/assets/7ea39f51-00d5-49e8-9c83-ac3605d98957)


 Select "continue" on osTicket browser. Enter helpdesk name and default email address.


![image](https://github.com/user-attachments/assets/ae1a3e17-29b2-45c7-a512-038445b06652)

![image](https://github.com/user-attachments/assets/ca9fe975-e6f8-4fe1-8140-20feb1974c0c)

![image](https://github.com/user-attachments/assets/2bf20d97-ad85-4e60-a2a4-72bdf2c364ac)


 Navigate the os-Ticket-Installations-Files folder, install HeidiSQL. After installation, open and create a new session with user and password both as “root”. Create a database called “osTicket” by right-clicking on “Unnamed”, create new, database.

 ![image](https://github.com/user-attachments/assets/2b0e015d-a53c-465d-b177-26ea1d7a1bcf)

 ![image](https://github.com/user-attachments/assets/36086aeb-3ff3-4fc0-b874-38b0c55ec7e7)


 After creating the database, navigate the the osTicket browser and enter credentials. Select "Install now". osTicket is now installed.












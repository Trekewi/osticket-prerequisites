Note: currently sourcing images and creating
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Enable IIS (Ineternet Information Services)
- Install Web Platform
- Install MySQL, SETUP username and password
- Install C++ Redistributable
- Configure Permissions, Install osTicket

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

- 1. Create an Azure Virtual Machine Windows 10, 4 vCPUs

- 2.	Open control panel, Programs -> turn off features or apps -> Install / Enable IIS in Windows WITH CGI (Enable Web management Tools + World Wide Web Services, you won't be able to open up IIS after installing these)

- 3.	From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) 
https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view?usp=share_link

- 4.	From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi) 
https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view?usp=share_link

- 5.	Create the directory C:\PHP (New folder in C:\PHP)

- 6.	From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view?usp=share_link

- 7.	From the Installation Files, download and install VC_redist.x86.exe.
https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view?usp=share_link

- 8.	From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view?usp=share_link
Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration ->
Password1 (Don't use this passsword, use a different one, note it down)

- 9.	Open IIS as an Admin

- 10.	Register PHP from within IIS

- 11.	Reload IIS (Open IIS, Stop and Start the server)

- 12. Install osTicket v1.15.8
a. Download osTicket from the Installation Files Folder
b. Extract and copy “upload” folder to c:\inetpub\wwwroot
c. Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

- 13.	Reload IIS (Open IIS, Stop and Start the server)
Go to sites -> Default -> osTicket
On the right, click “Browse *:80 (http)”

- 14.	Note that some extensions are not enabled
⦁	Go back to IIS, sites -> Default -> osTicket
⦁	Double-click PHP Manager
⦁	Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
⦁	Refresh the osTicket site in your browse, observe the changes

- 15. Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

- 16. Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

- 17. Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk ("Skylight" Help Desk)
Default email (receives email from customers)
(example)@helper.com

- 18. From the Installation Files, download and install HeidiSQL.
https://docs.google.com/document/d/1WovrX2DaS9xkfaSr4LXyB4YnnWpXIgPCMMbbfgHmGVw/edit
- Open Heidi SQL
- Create a new session, root/Password1
- Connect to the session
- Create a database called “osTicket”

- 19. Continue Setting up osticket in the browser
a.	MySQL Database: osTicket
b.	MySQL Username: root
c.	MySQL Password: Password1
d.	Click “Install Now!”

- Congratulations, hopefully it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

- End Users osTicket URL:
http://localhost/osTicket/

- Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php

- Notes:
Browse to your help desk login page: http://localhost/osTicket/scp/login.php  
End Users osTicket URL: http://localhost/osTicket/


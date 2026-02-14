<img width="1095" height="341" alt="Screenshot 2026-02-13 085051" src="https://github.com/user-attachments/assets/351fdf6d-55f8-46e8-948a-d06929245635" />



<h1>osTicket: Installation</h1>

<p img width="1356" alt="osTicket" src="images/osTicket Logo.png" />
</p>

<p>
This project outlines the process of installing a self-hosted osTicket help desk system on Windows. It marks the first installment of a three-part series that will cover installation, configuration, and ticket lifecycle management. The emphasis is on deploying osTicket using modular infrastructure components instead of relying on a single bundled installer. This approach highlights the preparation and integration of the web server, scripting runtime, and database necessary for the application. Establishing this foundational setup creates a robust environment for future projects, which will delve into system configuration and practical ticket workflows.</p>

<h2>2. Technologies Used</h2>

<p align="left">
<img src="https://skillicons.dev/icons?i=azure,windows,php,mysql" />&nbsp;&nbsp;<img src="images/osticket-icon-dark.png" width="48"></p>

 - Internet Information Services (IIS)
 - PHP
 - MySQL
 - Azure

<h2>3. Operating Systems</h2>

- Windows 10/11 Enterprise 22H2

<h2>4. High-Level Deployment Overview</h2>

- Configure the Windows Server environment by installing and enabling the required Web Server (IIS) roles and supporting features.

- Install and configure the PHP runtime along with all necessary extensions and dependencies to ensure compatibility with osTicket.

- Deploy and configure the database server (MySQL or MariaDB) to serve as the backend for storing osTicket data.

- Integrate all components and complete the web-based installation, finalizing the osTicket setup and validating system functionality.
  

<h2>5. Deployment & Installation Steps</h2>
Download Installation files: https://drive.google.com/file/d/1D4v2vQkaHXbWNHPZVXbRT2oAi1U71HpK/view?usp=drive_link
<h3>1. CREATE VM IN AZURE</h3>
Create an Azure Virtual Machine with the following settings.

- Name: vm-osticket
- Operating System: Windows 10 Enterprise 22H2
- Size: 4vCPUs, 32GB Ram
- Username: labuser
- Password: Password123!

> [!NOTE]
> Passwords are shown in this tutorial for learning purposes only. In real-world environments, it is never good practice to store passwords in plain text, credentials should always be managed securely using a password manager.

<h3>1. ENABLE IIS WEB SERVICES AND CGI</h3>
Use Remote Desktop Connect(RDP) to the new created VM, download the osTicket-Installation-Files.zip from the repo and unzip the whole folder unto your VM desktop. Search the start menu for Control Panel and click open and then "Turn Windows features on or off". Once the pop-up box comes up, find Internet Information Services and mark the checkbox. Expand World Wide Web > Expand Application Development Features, find CGI and mark the checkbox, and select OK and wait for features to be installed.

<details><summary>See screenshots</summary>
<img src="images/Step 2a.PNG" width="40%" >
</details> 

> [!NOTE]
> Internet Information Services (IIS) is the web server that will host the osTicket application.


<h3>2. INSTALL PHP MANAGER AND PREREQUISITES</h3>
A. Install PHP Manager for IIS

Locate PHPManagerForIIS_V1.5.0.msi in the installation folder and run the installer to complete the setup.

>![Note]
>osTicket is a PHP-based web application. PHP Manager enables IIS to properly process and manage PHP files, ensuring the application runs correctly. This step also helps manage PHP configuration settings and maintain version compatibility with osTicket.

B. Install IIS URL Rewrite Module
>From the installation folder, locate rewrite_amd64_en-US.msi and proceed with the installation.
>![Note]
>osTicket relies on URL rewriting for proper navigation and functionality. The IIS URL Rewrite Module allows the server to correctly interpret and process rewritten URLs required by the application.

C. Install the PHP Runtime
Create a new folder on the C:\ drive named PHP.
From the installation folder, extract the contents of php-7.3.8-nts-Win32-VC15-x86.zip into the newly created C:\PHP directory.
The extracted files contain the actual PHP runtime engine that IIS will execute. PHP Manager, installed earlier, is used to configure and manage this runtime environment.

D. Install Visual C++ Redistributable
Locate VC_redist.x86.exe in the installation folder and run the installer.
The Microsoft Visual C++ Redistributable package is required because PHP depends on these runtime libraries to function properly on Windows systems.

E. Install and Configure MySQL Server
Locate mysql-5.5.62-win32.msi in the installation folder and begin the installation process.
Select Typical Installation
Click Install
After installation completes, launch the MySQL Configuration Wizard

Within the wizard:

Choose Standard Configuration

Continue selecting Next until you reach the Modify Security Settings screen

Set both the username and password to:
root

Proceed by selecting Next

Click Execute

Finish the configuration

MySQL serves as the database backend for osTicket, storing tickets, user information, and all system-related data.

<details open><summary>See screenshots</summary>
<img src="images/Step 3 Ea.PNG" width="40%" > <img src="images/Step 3 Eb.PNG" width="40%" >
</details> 

<h3>3. REGISTER PHP WITH IIS</h3>
Search the start menu for "IIS", right-click and <b>Run as Admin</b>. Select Register New PHP Version. In the pop-up, select the three dots and browse to the <code>C:\PHP</code> folder, select the <code>php-cgi</code> file, and select OK.  We'll reload IIS by restarting the web server. On the left side under Connections, right-click the vm and select Stop, right-click vm again and select Start, minimize IIS Manager as we will come back to it.

<details><summary>See screenshots</summary>
<img src="images/Step 4a.PNG" width="50%" >
</details> 

<h3>5. ENABLE OSTICKET FEATURES AND ASSIGN CONFIG PERMISSIONS</h3>
In our installation folder, find <code>osTicket-v1.15.8.zip</code>, right-click and select Extract All, and then Extract. In the extracted folder, find and copy the upload folder to destination <code>C:inetpub\wwwroot</code>. Rename the upload folder to "osTicket" (no space, and uppercase T).

<details><summary>See screenshots</summary>
<img src="images/Step 5a.PNG" width="50%" >
</details> 

Reload IIS by restarting the web server again, stop and start instructions from Step 3 and minimize IIS Manager. Now in your web browser, navigate to "http://localhost/osticket/setup/".

<details><summary>See screenshots</summary>
<img src="images/Step 5b.PNG" width="50%" >
</details> 

Notice some features are not enabled here, we'll enable them next. Back in our IIS Manager, expand Site, expand Default Web Site and select folder osTicket.  Double-click PHP Manager, and select Enable or Disable an extension. 

- Enable php_imap.dll
- Enable php_intl.dll
- Enable php_opcache.dll

<details><summary>See screenshots</summary>
<img src="images/Step 5c.PNG" width="33%" > <img src="images/Step 5d.PNG" width="33%" ><img src="images/Step 5e.PNG" width="33%" >
</details> 

Refresh the osTicket site in the web browser and notice the changes.
Now we will be assigning permissions. Go to folder <code>C:\inetpub\wwwroot\osTicket\include</code> and find file <code>ost-sampleconfig.php</code>. Rename this file to <code>ost-config.php</code>. Now right-click file and select Properties. In Security tab, go to Advanced. Select Disable inhertiance > Remove all inhertied permissions. We are stripping away all current permissions here.

<details><summary>See screenshots</summary>
<img src="images/Step 5f.PNG" width="50%" >
</details> 


And then  we'll add permissions, select Add, Select Principles, in the object name text field, type, "Everyone" and then Check Names to underline our group and select OK. For basic permissions, select Full Control and OK.

<details><summary>See screenshots</summary>
<img src="images/Step 5g.PNG" width="33%" > <img src="images/Step 5h.PNG" width="33%" >
</details> 

> [!NOTE]
> Assigning Everyone permissions to ost-config.php is insecure because it allows unrestricted access to a sensitive configuration file. This is done temporarily in this lab to avoid installation issues; permissions should be restricted after setup in real environments.

<h3>6. INSTALL HEIDISQL AND CONFIGURE SQL</h3>

Back in the web browser, we will continue the osTicket setup, select Continue >> near the bottom. 
In System Settings, enter the help desk name and default email. In Admin User, enter admin name and admin email address, for username and password, we will set it to adminuser and <code>Password123!</code>. 

Before we select Install Now, we will need to configure our SQL and create the database and connection that osTicket will use.

<details><summary>See screenshots</summary>
<img src="images/Step 6a.PNG" width="50%" >
</details> 

Back in the installation folder, find <code>HeidiSQL_12.3.0.6589_Setup.exe</code>, and install it with all default settings, and select Finish to launch HeidiSQL. Select Skip, in this Session Manager window, Select +New, and type <code>root</code> for the password here, and select Open. Right-click the Unnamed session, and select Create new, and select Database. Enter for Name: osTicket (no space and capital T), and select OK.

<details><summary>See screenshots</summary>
<img src="images/Step 6b.PNG" width="40%" > <img src="images/Step 6c.PNG" width="40%" >
</details> 

Back in the web browser, we will continue the osTicket setup. Enter the following
- MySQL Database: osTicket
- MySQL Username: root
- MySQL Password: root
- **Select Install Now**

<details><summary>See screenshots</summary>
<img src="images/Step 6d.PNG" width="50%" >
</details> 

<h3>7. VERIFY INSTALLTION AND FUNCTIONAILTY</h3>
Congratulations, refer to the screenshots to ensure functionality!
For Admin/Analyst/Agent Login: http://localhost/osTicket/scp/login.php
For End User to create tickets: http://localhost/osTicket/

<details><summary>See screenshots</summary>
<img src="images/Step 7a.PNG" width="30%" > <img src="images/Step 7b.PNG" width="30%" > <img src="images/Step 7c.PNG" width="30%" >
</details> 






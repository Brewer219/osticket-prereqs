<img width="695" height="341" alt="Screenshot 2026-02-13 085051" src="https://github.com/user-attachments/assets/351fdf6d-55f8-46e8-948a-d06929245635" />



<h1>osTicket: Installation</h1>

<p img width="1356" alt="osTicket" src="images/osTicket Logo.png" />
</p>

<p>
This project outlines the process of installing a self-hosted osTicket help desk system on Windows. It marks the first installment of a three-part series that will cover installation, configuration, and ticket lifecycle management. The emphasis is on deploying osTicket using modular infrastructure components instead of relying on a single bundled installer. This approach highlights the preparation and integration of the web server, scripting runtime, and database necessary for the application. Establishing this foundational setup creates a robust environment for future projects, which will delve into system configuration and practical ticket workflows.</p>

<h2> Technologies Used</h2>

<p align="left">
<img src="https://skillicons.dev/icons?i=azure,windows,php,mysql" />&nbsp;&nbsp;
 
 - Web Server:  Internet Information Services (IIS)
 - Scripting Language: PHP
 - Database: MySQL
 - Cloud Platform: Azure
 - Operating Systems: Windows Pro 11

<h2> Operating Systems</h2>

- Windows 10/11 Enterprise 22H2

<h2> High-Level Deployment Overview</h2>

1. Configure Windows Server: Install and enable required IIS roles and features. 

2. Install PHP: Set up the PHP runtime and necessary extensions.

3. Deploy Database: Set up MySQL which plays as the data backend.
   
4. Integrate Components: Complete the web-based installation of osTicket.
  

<h2>Deployment & Installation Steps to Create Azure Virtual Machine</h2>

Create an Azure Virtual Machine with the following settings.
1. Create an Resource Group: Log into Azure and create a new resource group.
2. Then Create an Virtual Network: Set up a virtual network with default IPv4.
3. Create a Virtual Machine with inputting in the Fields:
- Give Name: osticket-vm
- Operating System: Windows 11 Pro
- Size: 4vCPUs, 32GB Ram
- Username: labuser
- Password: osTicketPassword1!

> Important To NOTE: Credentials need to manage securely using a password manager.


<h3>ENABLE IIS WEB SERVICES AND CGI</h3>
1.Use Remote Desktop Connect(RDP): Connect to the Viual Machine.
2.Download osTicket Files: Retrieve osTicket-Installation-Files.zip and unzip on the desktop.
3.Access Control Panel: Go to "Turn Windows features on or off" 
4. Enable IIS: Check mark Internet Information Services and expand "World Wide Web > Application Development Features" to enable CGI. Click OK to install.


> [!NOTE]: Internet Information Services (IIS) serves as the web server that host the osTicket application.


<h4> INSTALL PHP MANAGER AND PREREQUISITES</h4>
1. Install PHP Manager: For IIS Locate PHPManagerForIIS_V1.5.0.msi in the installation folder and run the installer.
>![Note]
>osTicket is a PHP-based web application. PHP Manager enables IIS to properly process and manage PHP files, ensuring the application runs correctly. This step also helps manage PHP configuration settings and maintain version compatibility with osTicket. 












<img width="325" height="317" alt="Step 7 Download PHPManagerIIS_v1 5 0 msi" src="https://github.com/user-attachments/assets/99911f35-19e3-4c63-bf36-6c42b988300c" />




























 <h5>Install IIS URL Rewrite Module</h5> 
 1. Locate rewrite_amd64_en-US.msi and proceed with installation.
 2. >[!Note]: osTicket relies on URL rewriting for proper navigation and functionality. 
 3. Install the PHP Runtime
 4. Create PHP Directory: Create a folder and name it "PHP" on the C:\drive.
 5. Extract PHP Files: 'php-7.3.8-nts-Win32-VC15-x86.zip' into the newly created C:\PHP directory.
 6. Install Visual C++ Redistributable: Run 'VC_redist.x86.exe' to install the neccessary libraries.
   
 >[!NOTE] PHP Manager, installed earlier, is used to configure and manage this runtime environment.














<h5>Install and Configure MySQL Server</h5>
1. Run MySQL Installer: Locate 'mysql-5.5.62-win32.msi' and initiate installation folder and begin the installation process.
2. Select Typical Installation: Click Install and launch the MySQL Configuration Wizard.
3. Configuration Wizard: Choose Standard Configuration and set both the username and password to 'root'. Then Finish the setup.
17. After installation completes, launch the MySQL Configuration Wizard

Within the wizard:

Choose Standard Configuration

Continue selecting Next until you reach the Modify Security Settings screen

Set both the username and password to:
root

Proceed by selecting Next

Click Execute

Finish the configuration

MySQL serves as the database backend for osTicket, storing tickets, user information, and all system-related data.


<img width="366" height="438" alt="Step 9 MySQL sever 5 5 62" src="https://github.com/user-attachments/assets/ef6ffde0-2637-44a8-afd9-525fba79f045" />
























<h6>REGISTER PHP WITH IIS</h6>
1. Open IIS Manager: Search for IIS, right-click, and select Run as Administrator.
2. Register PHP: Select "Register New PHP Version" and browse to C:/PHP to select 'php-cgi.exe'.
3. Restart IIS: Stop and start the web server to apply changes.





<h7>ENABLE OSTICKET FEATURES AND ASSIGN CONFIG PERMISSIONS</h7>
1. Extract osTicket Files: Extract 'osTicket-v1.15.8.zip' and copy the 'upload' folder to'C:\inetpub\wwwroot', renaming it to 'osTicket'.
2. Enable PHP Extensions: In IIS Manager, enable the following:
 -'php_imap.dll'
 -'php_intl.dll'
 -'php_opcache.dll'
3. Configure File Permissions: Rename 'ost-sampleconfig.php' to 'ost-config.php', right-click and set permissions for "Everyone" temporarily.


[!Important]: This is insecure and should be restricted in real production environments. Assigning Everyone permissions to ost-config.php is insecure because it allows unrestricted access to a sensitive configuration file. This is done temporarily in this lab to avoid installation issues; permissions should be restricted after setup in real environments.





4. Reload IIS by restarting the web server again, stop and start instructions from Step 3 and minimize IIS Manager. Now in your web browser, navigate to "http://localhost/osticket/setup/".

  





5. Refresh the osTicket site in the web browser and notice the changes.
Now we will be assigning permissions. Go to folder <code>C:\inetpub\wwwroot\osTicket\include</code> and find file <code>ost-sampleconfig.php</code>. Rename this file to <code>ost-config.php</code>. Now right-click file and select Properties. In Security tab, go to Advanced. Select Disable inhertiance > Remove all inhertied permissions. We are stripping away all current permissions here.






And then  we'll add permissions, select Add, Select Principles, in the object name text field, type, "Everyone" and then Check Names to underline our group and select OK. For basic permissions, select Full Control and OK. 


<img width="324" height="411" alt="Step 16 ost- hit apply then okay" src="https://github.com/user-attachments/assets/cb4f5a96-5e1e-4a4d-8c3a-360114de1a53" />














<h8>INSTALL HEIDISQL AND CONFIGURE SQL</h8>

Before we select Install Now, we will need to configure our SQL and create the database and connection that osTicket will use.


1. Install HeidiSQL: Run 'HeidoSQL_12.3.0.6589_Setup.exe' with default settings.
2. Create Database: Connect using 'root' as the password, create a database named 'osTicket'.

3. The osTicket setup, select Continue >> near the bottom. 
4. In System Settings, enter the help desk name and default email.
5. In Admin User, enter admin name and admin email address, for username and password, we will set it to adminuser and <code>Password1</code>.
6. Back in the installation folder, find <code>HeidiSQL_12.3.0.6589_Setup.exe</code>, and install it with all default settings, and select Finish to launch HeidiSQL.
7. Select Skip, in this Session Manager window, Select +New, and type <code>root</code> for the password here, and select Open.
8. Right-click the Unnamed session, and select Create new, and select Database. Enter for Name: osTicket (no space and capital T), and select OK.

   <img width="322" height="442" alt="Step 15 Hedi" src="https://github.com/user-attachments/assets/25424f30-3efe-4783-a158-f167eaa04475" />
















 

<h9>Finalize osTicket Setup</h9>
1. Continue Installation: Navigate to 'https://localhost/osticket/setup/'
Back in the web browser, we will continue the osTicket setup. Enter the following
- MySQL Database Settings: 'osTicket'
- MySQL Username: 'root'
- MySQL Password: 'root'
- Complete Installation: "Select Install Now" button
  

<img width="341" height="464" alt="Step 17 Hedi osTicket Install Admin" src="https://github.com/user-attachments/assets/3710b3b0-e332-45c0-9342-e88a132be198" />












<h10> VERIFY INSTALLTION AND FUNCTIONAILTY</h10>
Congratulations, refer to the screenshots to ensure functionality!
- Admin Login: http://localhost/osTicket/scp/login.php
- For End User to create tickets: http://localhost/osTicket/

  
<img width="319" height="405" alt="Step 3 Admin Staff Control" src="https://github.com/user-attachments/assets/68b0fa66-763e-4b3f-8985-09dc3fbd7777" />














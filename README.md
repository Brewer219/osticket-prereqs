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
  

<h2> Deployment & Installation Steps to Create Azure Virtual Machine</h2>

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


<h3> ENABLE IIS WEB SERVICES AND CGI</h3>
1.Use Remote Desktop Connect(RDP): Connect to the Viual Machine.
2.Download osTicket Files: Retrieve osTicket-Installation-Files.zip and unzip on the desktop.
3.Access Control Panel: Go to "Turn Windows features on or off" 
4. Enable IIS: Check mark Internet Information Services and expand "World Wide Web > Application Development Features" to enable CGI. Click OK to install.


> [!NOTE]: Internet Information Services (IIS) serves as the web server that host the osTicket application.


<h4> INSTALL PHP MANAGER AND PREREQUISITES</h4>
1. Install PHP Manager: For IIS Locate PHPManagerForIIS_V1.5.0.msi in the installation folder and run the installer.
>![Note]
>osTicket is a PHP-based web application. PHP Manager enables IIS to properly process and manage PHP files, ensuring the application runs correctly. This step also helps manage PHP configuration settings and maintain version compatibility with osTicket.

2. Install IIS URL Rewrite Module: Locate rewrite_amd64_en-US.msi and proceed with installation.
3. >[!Note]: osTicket relies on URL rewriting for proper navigation and functionality. 
4. Install the PHP Runtime
6. Create PHP Directory: Create a folder and name it "PHP" on the C:\drive.
7. Extract PHP Files: 'php-7.3.8-nts-Win32-VC15-x86.zip' into the newly created C:\PHP directory.
8. Install Visual C++ Redistributable: Run 'VC_redist.x86.exe' to install the neccessary libraries.
   
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

 <img width="414" height="424" alt="Step 5 MySQL server 5 5 62" src="https://github.com/user-attachments/assets/7f022776-cafe-4569-897e-521c9b347239" />
<img width="366" height="438" alt="Step 9 MySQL sever 5 5 62" src="https://github.com/user-attachments/assets/9abbacdd-28da-471c-ad49-fe8a313af72c" />



<h6> REGISTER PHP WITH IIS</h6>
1. Open IIS Manager: Search for IIS, right-click, and select Run as Administrator.
2. Register PHP: Select "Register New PHP Version" and browse to C:/PHP to select 'php-cgi.exe'.
3. Restart IIS: Stop and start the web server to apply changes.
<img width="341" height="353" alt="Step 1 Open IIS" src="https://github.com/user-attachments/assets/2447e8f0-7160-423d-8f11-9303bd6f6d19" /><img width="329" height="391" alt="Step 3 Register PHP" src="https://github.com/user-attachments/assets/92c901ae-1f4f-4891-b5aa-8fd3cc0a68de" />
<img width="979" height="647" alt="Step 5 complete php cgi binary" src="https://github.com/user-attachments/assets/b4cb6ecf-3dc6-4b4a-904b-f820bf7bc790" />




<h7>ENABLE OSTICKET FEATURES AND ASSIGN CONFIG PERMISSIONS</h7>
1. Extract osTicket Files: Extract 'osTicket-v1.15.8.zip' and copy the 'upload' folder to'C:\inetpub\wwwroot', renaming it to 'osTicket'.
2. Enable PHP Extensions: In IIS Manager, enable the following:
 -'php_imap.dll'
 -'php_intl.dll'
 -'php_opcache.dll'
3. Configure File Permissions: Rename 'ost-sampleconfig.php' to 'ost-config.php', right-click and set permissions for "Everyone" temporarily.
<img width="300" height="341" alt="Step 1 Install osTicket v1 15 8" src="https://github.com/user-attachments/assets/b623b14e-0e4e-4ae6-8559-ebb017679c1c" /><img width="358" height="470" alt="Step 2 Extract v1 15 8" src="https://github.com/user-attachments/assets/27aab5f9-54bf-42db-aa79-c7a8b64caee2" /><img width="302" height="475" alt="Step 3 osTicket v1 15 8 inside of the folder" src="https://github.com/user-attachments/assets/3748397f-ff8f-43fb-ba3f-fbf48e56b1e8" /><img width="333" height="629" alt="Step 6 v1 15 8 osTicket" src="https://github.com/user-attachments/assets/044d53dd-f215-4888-b03d-96353d229ea7" /><img width="351" height="428" alt="Step 9 v1 15 8 rename osTicket inside wwwroot" src="https://github.com/user-attachments/assets/e0700260-70c4-4e21-9d13-2ad0956c16f7" />

[!Important]: This is insecure and should be restricted in real production environments. Assigning Everyone permissions to ost-config.php is insecure because it allows unrestricted access to a sensitive configuration file. This is done temporarily in this lab to avoid installation issues; permissions should be restricted after setup in real environments.





4. Reload IIS by restarting the web server again, stop and start instructions from Step 3 and minimize IIS Manager. Now in your web browser, navigate to "http://localhost/osticket/setup/".<img width="1074" height="444" alt="Step 11 v1 15 8 osTicket RESTART button Hit" src="https://github.com/user-attachments/assets/9d5a7b6b-d8ad-49b5-8a40-75967f25e734" />
 

  
<img width="328" height="380" alt="Step 18 v1 15 8 PHP ext 1" src="https://github.com/user-attachments/assets/29d15207-e87d-4209-8cd1-174b6c986e3e" /> <img width="328" height="685" alt="Step 19 v1 15 8 PHP ext 2" src="https://github.com/user-attachments/assets/90327b6f-1e7d-43c3-9ab2-a8c80f00ec05" /> <img width="328" height="385" alt="Step 20 v1 15 8 PHP ext 3" src="https://github.com/user-attachments/assets/54f31f74-1d04-4555-a5b4-f78350646e3e" />




5. Refresh the osTicket site in the web browser and notice the changes.
Now we will be assigning permissions. Go to folder <code>C:\inetpub\wwwroot\osTicket\include</code> and find file <code>ost-sampleconfig.php</code>. Rename this file to <code>ost-config.php</code>. Now right-click file and select Properties. In Security tab, go to Advanced. Select Disable inhertiance > Remove all inhertied permissions. We are stripping away all current permissions here.
<img width="387" height="361" alt="CopyPaste PHP folder inside C;" src="https://github.com/user-attachments/assets/518c05fa-1237-4811-acda-203b42666127" /><img width="364" height="435" alt="Step 8 v1 15 8 finishing with copy upload folder into wwwroot" src="https://github.com/user-attachments/assets/0403b5e2-e249-41af-a2ef-14ab46bfb8e2" /><img width="351" height="328" alt="Step 9 v1 15 8 rename osTicket inside wwwroot" src="https://github.com/user-attachments/assets/2505834b-4796-47f7-b9d8-496891f576a3" /><img width="493" height="252" alt="Step 4 get inside include folder" src="https://github.com/user-attachments/assets/7f567f51-6b60-47b8-98e1-481b75d3034b" /><img width="328" height="344" alt="ost-config php inside include part 1" src="https://github.com/user-attachments/assets/5c4a6bf0-9446-45af-8e65-6c2843364062" />








And then  we'll add permissions, select Add, Select Principles, in the object name text field, type, "Everyone" and then Check Names to underline our group and select OK. For basic permissions, select Full Control and OK. <img width="552" height="331" alt="Step 10 ost- Permission tab" src="https://github.com/user-attachments/assets/49579279-0a31-4a57-a0c3-4c6ffed0c10c" /> <img width="440" height="487" alt="Step 11 ost- add new permission" src="https://github.com/user-attachments/assets/b7fda07b-63db-4fd0-93d7-1c2541c5f21d" /><img width="337" height="490" alt="Step 13 ost-" src="https://github.com/user-attachments/assets/c157ff08-85da-40f9-8354-e027cb7b1a4d" /><img width="309" height="453" alt="Step 15 ost-" src="https://github.com/user-attachments/assets/614cf907-2d08-440c-ab4d-f42aaf44e110" />



<h8>INSTALL HEIDISQL AND CONFIGURE SQL</h8>
Before we select Install Now, we will need to configure our SQL and create the database and connection that osTicket will use.
<img width="342" height="299" alt="Step 1 click on Hedi" src="https://github.com/user-attachments/assets/fcd89bec-a455-4173-872f-02caa0e5b705" />

1. Install HeidiSQL: Run 'HeidoSQL_12.3.0.6589_Setup.exe' with default settings.
2. Create Database: Connect using 'root' as the password, create a database named 'osTicket'.

3. The osTicket setup, select Continue >> near the bottom. 
4. In System Settings, enter the help desk name and default email.
5. In Admin User, enter admin name and admin email address, for username and password, we will set it to adminuser and <code>Password1</code>.
6. Back in the installation folder, find <code>HeidiSQL_12.3.0.6589_Setup.exe</code>, and install it with all default settings, and select Finish to launch HeidiSQL.
7. Select Skip, in this Session Manager window, Select +New, and type <code>root</code> for the password here, and select Open.
8. Right-click the Unnamed session, and select Create new, and select Database. Enter for Name: osTicket (no space and capital T), and select OK.

 
<img width="314" height="240" alt="Step 12 Hedi" src="https://github.com/user-attachments/assets/ba3a47ab-56b7-4044-90f8-219a2d59c31f" /><img width="322" height="442" alt="Step 15 Hedi" src="https://github.com/user-attachments/assets/60fe0227-8bce-4451-8e0a-34e842102fb7" />



<img width="342" height="299" alt="Step 1 click on Hedi" src="https://github.com/user-attachments/assets/fcd89bec-a455-4173-872f-02caa0e5b705" />
<h9>Finalize osTicket Setup</h9>
1. Continue Installation: Navigate to 'https://localhost/osticket/setup/'
Back in the web browser, we will continue the osTicket setup. Enter the following
- MySQL Database Settings: 'osTicket'
- MySQL Username: 'root'
- MySQL Password: 'root'
- Complete Installation: "Select Install Now" button
  
<img width="385" height="333" alt="Step 7 Hedi" src="https://github.com/user-attachments/assets/26beb034-6e29-4cf0-8028-af55a6b959f0" /><img width="367" height="319" alt="Step 8 Hedi" src="https://github.com/user-attachments/assets/729d9909-1e8b-4225-9a2b-d378112fb02a" />




<h10> VERIFY INSTALLTION AND FUNCTIONAILTY</h10>
Congratulations, refer to the screenshots to ensure functionality!
- Admin Login: http://localhost/osTicket/scp/login.php
- For End User to create tickets: http://localhost/osTicket/





<img width="319" height="305" alt="Step 3 Admin Staff Control" src="https://github.com/user-attachments/assets/3fa99120-58ea-4ca5-87a8-ee401c1e9279" /> <img width="322" height="389" alt="For end user to put in support ticket part 4" src="https://github.com/user-attachments/assets/438391d6-4033-4658-8eae-676432cedea1" />








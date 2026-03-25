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
2. Create a Virtual Machine with inputting in the Fields:
- Give Name: osticket-vm
- Operating System: Windows 11 Pro
- Size: 4vCPUs, 32GB Ram
- Username: labuser
- Password: osTicketPassword1!

> Important To NOTE: Credentials needs to be manage securely using a password manager.
<details><summary>See screenshots</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details> 

 
## 1. Creating Resource Group
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details>

<img width="328" height="485" alt="osTicket creating a Resource Group" src="https://github.com/user-attachments/assets/f0202a8d-f5b1-4ada-afa9-82ec18eb92c6" />


## 2. Click Review+Create Button
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details>

<img width="321" height="467" alt="osTicket then click last button Create" src="https://github.com/user-attachments/assets/81eb03f6-c997-4b76-bd77-7f63baaa16fb" />

## 3. Then Click the Create Button to Deploy the Resource Group
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details>

<img width="321" height="467" alt="osTicket then click last button Create" src="https://github.com/user-attachments/assets/ef7b6d95-a8ff-494d-8177-043056abd6be" />

## 4. Create an Virtual Machine In Azure for osTicket
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details>

<img width="321" height="467" alt="Click the &#39;Create&#39; button for Virtual Machine for osTicket" src="https://github.com/user-attachments/assets/b8cb1840-83a0-4782-9bd3-188bd14b9967" />

## 5. Creating osTicket Virtual Machine In Azure in the Basics Tab
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details>

<img width="321" height="467" alt="Creating osTicket VM " src="https://github.com/user-attachments/assets/9a803390-5776-46d9-a571-9918c42d9b94" />


## 6. Fill Out The Fields For Image and Size
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details>

<img width="321" height="467" alt="osTicket vm image and size fields already selected" src="https://github.com/user-attachments/assets/46dbb9aa-b2f1-450e-b008-44d950e742d9" />

## 7. Creating An Administrator Account For osTicket Virtual Machine
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details>

<img width="321" height="467" alt="osTicket creating credentials for to log into vm machine" src="https://github.com/user-attachments/assets/dab0b5fb-ab86-40c0-91ab-4cfc2e97c4c7" />

## 8. For osTicket VM Clicking On the License Box to Confirm Licensing and Click On Disk Tab
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details>
<img width="321" height="467" alt="osTicket vm creating confirm licensing by checkbox" src="https://github.com/user-attachments/assets/46c0f6e1-d0cb-4df8-8a7e-ad761eaed611" />

## 9. From Disk Tab Click On Networking Tab
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details>

<img width="321" height="467" alt="osTicket vm Networking tab make sure subnet is default and virtual network correct" src="https://github.com/user-attachments/assets/4d172549-f615-468d-9487-02b23a41e7e6" />

## 10. From There On The Networking Tab make sure The Subnet is Default And Then Click Review+Create Button
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details>
<img width="322" height="467" alt="osTicket vm Networking tab make sure subnet is default and virtual network correct" src="https://github.com/user-attachments/assets/e2b7af51-6edc-429b-a630-8b2719c7d720" />

## 11. From There Click 'Create' Button to Deploy osTicket Virtual Machine Successfully
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details>

<img width="321" height="467" alt="osTicket leave Networking tab and hit ReviewCreate and then finally create VM for osTicket" src="https://github.com/user-attachments/assets/14728fe4-fcac-4a6f-a2f2-bc5eb28bc689" />

## 12. From There Type Inside the Search Bar 'Virtual Machine' And Press Enter
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details> 

<img width="321" height="467" alt="go to the Azure VM page and now checkmark and click osticketvm" src="https://github.com/user-attachments/assets/bfda7281-7525-43d7-b44a-5d693066469f" />

## 13. Click The 'osticket' Virtual Machine To Get Inside To Click The 'Connect' Button To Obtain the RDP file to Download the Remote Desktop Application 
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details> 


<img width="321" height="467" alt="osticketvm after clicking the Connect button click &#39;Download RDP file&#39;" src="https://github.com/user-attachments/assets/993ab991-c24c-47c0-8c75-8f99338fc02c" />

## 14. Allow 'osticket' Virtual Machine to Be downloaded from My Personal PC
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details> 

<img width="321" height="467" alt="osTicket VM the RDP file is Downloaded" src="https://github.com/user-attachments/assets/3d666453-c0a8-4d9c-8725-3ce816726916" />

## 15. Lastly Open the 'osticket-vm' And I type In Your Credentials to Login to Virtual Machine
<details><summary>See screenshot</summary>
<img src="images/Step 3a.PNG" width="60%" >
</details> 

<img width="321" height="467" alt="Logging into my osTicket vm with credentials or password" src="https://github.com/user-attachments/assets/998c4e61-adc3-45dd-8173-8d994f581353" />




















<h3>NEXT Process and Steps: ENABLE IIS WEB SERVICES AND CGI</h3>
- Now once log inside 'osticket-vm then Retrieve osTicket-Installation-Files.zip and unzip so it can be on the desktop.
- Type 'Windows + R and then Type 'Control' in the box to pullup Access Control Panel: 
- Once In Control Panel Then Go to "Turn Windows features on or off" 
- In Order To Enable IIS: Check mark Internet Information Services and expand "World Wide Web > Application Development Features" to Then Checkmark enable CGI. Click OK to install.



 ## 1. Downloading osTicket-Installation Files that Are Zipped

<details><summary>See screenshot</summary>

<img src="images/Step 2b.png" width="60%">
</details>
 

 <img width="321" height="467" alt="Opening up osTicket Installation zip file and then download it" src="https://github.com/user-attachments/assets/f93f3257-1b66-48bd-83f1-6e0e0af471b3" />

 ## 2. Then Unzip osTicket-Installation File onto Desktop By Right-Clicking to Extract it

 <details><summary>See screenshot</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="osTicket Installation Folder that actually truly unzip and files can be extracted" src="https://github.com/user-attachments/assets/a8ec57f3-276d-4618-bfb8-46ae5cd21913" />



> [!NOTE]: When it comes to Internet Information Services (IIS) it serves as the web server that host the osTicket application.
> Now Moving Along To Step....

## 3. To Enable IIS In Windows and CGI 
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="osTicket installing IIS by typing &#39;control&#39; in windows R box for pulling up control panel" src="https://github.com/user-attachments/assets/77b55e2d-d33e-45c3-9a75-93348ca62758" />

## 4. Once Inside The Control Panel Click 'Programs'

 <details><summary>See screenshot</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Once inside Control Panel then click on Programs" src="https://github.com/user-attachments/assets/cee86e92-abbb-4f05-92ca-ed03f7c13b16" />

## 5. Click or Select 'Windows features on or off' in the Control Panel 

<details><summary>See screenshot</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="osTicket Installation Inside Programs select Windowns features on or off" src="https://github.com/user-attachments/assets/bdbcb8f9-620e-4d2a-96e4-6428ce9af83b" />

## 6. Then Enable CGI Feature
> ### [!NOTE]: For The Next Steps and Procedures Make sure 'Internet Information Services' is checked box--->> Make Sure 'World Wide Web Service' is checkmarked and expand--->> Make Sure 'Application Development Features'  and expand it and then scroll down and look for CGI feature and checkbox it and click 'OK'.
 <details><summary>See screenshot</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="osTicket Installation check Internet Information Services, go to WWWS then click expand ADF then select CGI decepencies" src="https://github.com/user-attachments/assets/67d0a71b-a11c-4b6b-b284-2ed1a5811d70" />

## 7. IIS Internet Information Webserver is Finally Enable

 <details><summary>See screenshot</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="osTicket after installing CGI now IIS webserver in working now for the installation" src="https://github.com/user-attachments/assets/3f8bec2a-bda0-488f-a035-a320223dfce4" />








## <h4> Next Proccess: INSTALL PHP MANAGER AND PREREQUISITES</h4>
1.Install PHP Manager: For IIS Locate PHPManagerForIIS_V1.5.0.msi in the installation folder and run the installer.
osTicket is a PHP-based web application. PHP Manager enables IIS to properly process and manage PHP files, ensuring the application runs correctly.This step also helps manage PHP configuration settings and maintain version compatibility with osTicket. 

<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

## 1. Download the PHP Manager IIS_v1.5.0 File and ONLY accept the Licensing and click next and leave everything 'as is' and close application 

<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="PHPManager for IIS v1 0 5 hit NEXT" src="https://github.com/user-attachments/assets/d1b1b189-28db-4179-926e-8b9fa6419369" />

 



## <h5>Install IIS URL Rewrite Module And Create a PHP Folder in the C Drive</h5> 
 - Locate rewrite_amd64_en-US.msi and proceed with installation.
 - osTicket relies on URL rewriting for proper navigation and functionality. 
 - Install the PHP Runtime
 - Create PHP Directory: Create a folder and name it "PHP" on the C:\drive.
 - Extract PHP Files: 'php-7.3.8-nts-Win32-VC15-x86.zip' into the newly created C:\PHP directory.
 
   
 >[!NOTE] PHP Manager, installed earlier, is used to configure and manage this runtime environment.



## 1. Right-Click File Explorer and Click 'Windows C:' Drive

<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="osTicket Installation rightclick File Explorer and click Windows C drive" src="https://github.com/user-attachments/assets/63fe51df-a26e-4cae-a699-68a7abcb6b81" />

## 2. In The 'C:' Drive create a new folder and name it PHP

<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="osTicket Installation once in C drive name the new folder PHP" src="https://github.com/user-attachments/assets/70757d1d-17bc-4fdf-97a3-c0392691ab5b" />

## 3. Then go back to PHP 7.3.8 and click it
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="osTicket Installation folder click php 7 3 8 binary and right click extract it" src="https://github.com/user-attachments/assets/aa9462cd-561a-4592-aa04-1bf4cafea0ff" />

## 4. For PHP 7.3.8 unzip the file by right clicking it and selecting the 'Extract' option
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="osTicket Installation php 7 3 8 being extracted by clicking on PHP folder" src="https://github.com/user-attachments/assets/66608b9c-57a4-49ff-b781-c94e6a3b81d6" />

## 5. Then Browse and select the PHP folder that was recently created

<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="osTicket Installation once PHP folder is found in C drive and selected then click Extract button" src="https://github.com/user-attachments/assets/99ceca0c-f477-4979-a4ae-892bdd18bc79" />










## <h5>Install Visual C++ Redistributable</h5> 

## 1. Go back into osTicket-Installation Folder and click 'VC_redist.x86.exe' to install the neccessary libraries.

<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Next Install VC redist 86x" src="https://github.com/user-attachments/assets/78cce297-230e-481c-aedd-b8e5869e206e" />

## 2. In The Visual C++ below click 'agree to licensing terms and conditions'

<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="VC redist 86x C++ click the Licensing Box and click Install" src="https://github.com/user-attachments/assets/766021a2-8d52-4e68-8ac8-a96450601bce" />

## 3. This file will fully load and install and once it does then click 'Close'

<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="VC redist C++ once installed fully the click &#39;Close&#39; button" src="https://github.com/user-attachments/assets/d4d8e6cb-c5f0-402c-a737-139f8b46e876" />







  














## Install and Configure MySQL Server
## 1. Locate 'mysql-5.5.62-win32.msi' and initiate installation folder and begin the installation process.

  <details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>
   <img width="321" height="467" alt="Install mysql 5 5 62 for osTicket database" src="https://github.com/user-attachments/assets/eae6e8ee-f9fe-4a6b-9f3f-47b72672af32" />

   ## 2. Accept the Licensing and Terms for mysql-5.5.62
   
   <details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>
   
   
   <img width="321" height="467" alt="mysql 5 5 62 click licensing box then click next" src="https://github.com/user-attachments/assets/e295a21d-1623-4124-a7cb-c192de80dbac" />


   

   
## 3. Select Typical Installation: <details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="mysql server data base click &#39;Typical&#39;" src="https://github.com/user-attachments/assets/1906905c-86fe-4084-ad7d-411cca8a3533" />





## 4. Click Install and launch the MySQL Configuration Wizard.
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="mysql server database click Install button" src="https://github.com/user-attachments/assets/3aceda39-14e4-4777-90eb-cba4b5c265cc" />


## 5. Configuration Wizard: Select Standard Configuration Options<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="To launch mysql database configuration click the &#39;Standard&#39; option" src="https://github.com/user-attachments/assets/cba6c1d8-15c1-457d-874a-ee1c0b857916" />


## 6. Continue selecting Next until you reach the Modify Security Settings screenand set both the username and password to 'root'. Then Finish the setup.
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="mysql database typing in &#39;root&#39; but not good for business environment but leave everything as is" src="https://github.com/user-attachments/assets/2e2eb850-2c03-4442-974e-f5ff4ca42edd" />

   
 After installation completes, launch the MySQL Configuration Wizard


## 7. Proceed by selecting Next Click Execute
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="after typing &#39;root&#39; for password in mysql for configuration process then click the&#39;Execute&#39; button" src="https://github.com/user-attachments/assets/c807c715-fbe7-48e7-be26-7fb9dca7b9ab" />


## 8. Finish the configuration
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="mysql 5 5 62 once everything is checked off in processing configuration then click &#39;Finish&#39; button" src="https://github.com/user-attachments/assets/7a29c1bf-559c-4496-8e74-47b228e691b7" />


MySQL serves as the database backend for osTicket, storing tickets, user information, and all system-related data.


<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>


















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


<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>



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



<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>


   <img width="322" height="442" alt="Step 15 Hedi" src="https://github.com/user-attachments/assets/25424f30-3efe-4783-a158-f167eaa04475" />
















 

<h9>Finalize osTicket Setup</h9>
1. Continue Installation: Navigate to 'https://localhost/osticket/setup/'
Back in the web browser, we will continue the osTicket setup. Enter the following
- MySQL Database Settings: 'osTicket'
- MySQL Username: 'root'
- MySQL Password: 'root'
- Complete Installation: "Select Install Now" button.


<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>
  

<img width="341" height="464" alt="Step 17 Hedi osTicket Install Admin" src="https://github.com/user-attachments/assets/3710b3b0-e332-45c0-9342-e88a132be198" />












<h10> VERIFY INSTALLTION AND FUNCTIONAILTY</h10>
Congratulations, refer to the screenshots to ensure functionality!
- Admin Login: http://localhost/osTicket/scp/login.php
- For End User to create tickets: http://localhost/osTicket/


<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>
  
<img width="319" height="405" alt="Step 3 Admin Staff Control" src="https://github.com/user-attachments/assets/68b0fa66-763e-4b3f-8985-09dc3fbd7777" />














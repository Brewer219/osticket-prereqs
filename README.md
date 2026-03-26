<img width="695" height="341" alt="Screenshot 2026-02-13 085051" src="https://github.com/user-attachments/assets/351fdf6d-55f8-46e8-948a-d06929245635" />



<h1>osTicket: Installation</h1>

<p img width="1356" alt="osTicket" src="images/osTicket Logo.png" />
</p>

<p>
This project outlines the process of installing a self-hosted osTicket help desk system on Windows. It marks the first installment of a three-part series that will cover installation, configuration, and ticket lifecycle management. The emphasis is on deploying osTicket using modular infrastructure components instead of relying on a single bundled installer. This approach highlights the preparation and integration of the web server, scripting runtime, and database necessary for the application. Establishing this foundational setup creates a robust environment for future projects, which will delve into system configuration and practical ticket workflows.</p>

## <h2>Technologies Used</h2>

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
  

## <h3>Next Process: Deployment & Installation Steps to Create Azure Virtual Machine</h3>

Create an Azure Virtual Machine with the following settings.
1. Create an Resource Group: Log into Azure and create a new resource group.
2. Create a Virtual Machine with inputting in the Fields:
- Give Name: osticket-vm
- Operating System: Windows 11 Pro
- Size: 4vCPUs, 32GB Ram
- Username: labuser
- Password: osTicketPassword1!

> Important To NOTE: Credentials needs to be manage securely using a password manager.


 
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







## <h3>NEXT Process: ENABLE IIS WEB SERVICES AND CGI</h3>
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

 



### <h5>Next Process: Install IIS and  And Create a PHP Folder in the C Drive</h5> 
 -  Extract PHP Files: 'php-7.3.8-nts-Win32-VC15-x86.zip' into the newly created C:\PHP directory.
 -  From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.
 - osTicket relies on URL rewriting for proper navigation and functionality. 
 - Install the PHP Runtime
 - Create PHP Directory: Create a folder and name it "PHP" on the C:\drive.
 
 >[!NOTE] PHP Manager, installed earlier, is used to configure and manage this runtime environment.



 ## <h6>Next Process: Then Install URL Rewrite Module</h6>
# 1. Now how I locate rewrite_amd64_en-US.msi is by locating my unzip "osTicket-Installation-Files" from desktop and then double-clicking the file so the rewrite module box will pop-up as shown below:

<details><summary>See screenshot 1</summary>

<img src="images/Step 2b.png" width="60%">
</details>

   <img width="321" height="467" alt="osTicket Installation the inside look for rewrite file" src="https://github.com/user-attachments/assets/a3d2c890-072e-42bf-86c0-554edd8fc912" />

   ## 2. Once I double-click the file then the "IIS URL Rewrite Module 2 Setup" box will pop-up and from there I then checkbox the terms in the License Agreement to make sure I had accept license which is shown from image below:
   
<details><summary>See screenshot 2</summary>

<img src="images/Step 2b.png" width="60%">
</details>
   
<img width="321" height="467" alt="osTicket Installation folder once &#39;rewrite&#39; file is clicked the checkbox Licensing Agreement and click Install" src="https://github.com/user-attachments/assets/ac5bec51-23a8-4b19-ac09-0cf6f4473ae1" />

## 3. From there I proceed to click "Install" button and allow the 'rewrite_amd64_en-US" to install as shown from the image shown below:

<details><summary>See screenshot 3</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="osTicket Installaing Folder &#39;rewrite&#39; file is loading " src="https://github.com/user-attachments/assets/ce7bb055-619b-413e-b394-505e34685ce2" />

## 4. Once the rewrite file is completely installed then I also click the "finish" button once I was able to successfully install my "rewrite_amd64_en-US" as shown in the image shown below:

<details><summary>See screenshot 4</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="osTicket Installation folder &#39;rewrite&#39; file is finished installing now hit the the Finished button" src="https://github.com/user-attachments/assets/fcf99b68-2e4e-4cc1-8184-9aa49a176291" />





#### <h3>Next Process: Creation of PHP Folder</h3> 

## 1.To get to creating my PHP folder I right-click my File Explorer folder and then Click my 'Windows C:' Drive

<details><summary>See screenshot</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="osTicket Installation rightclick File Explorer and click Windows C drive" src="https://github.com/user-attachments/assets/63fe51df-a26e-4cae-a699-68a7abcb6b81" />

## 2. In my 'C:' Drive I proceed to create a new folder  by right-clicking a random spot and choose create 'new folder' and then I name it PHP

<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="osTicket Installation once in C drive name the new folder PHP" src="https://github.com/user-attachments/assets/70757d1d-17bc-4fdf-97a3-c0392691ab5b" />

## 3. Then I go back to osTicket-Installation-File that's unzipped where PHP 7.3.8 
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="osTicket Installation folder click php 7 3 8 binary and right click extract it" src="https://github.com/user-attachments/assets/aa9462cd-561a-4592-aa04-1bf4cafea0ff" />

## 4. For PHP 7.3.8 unzip the file by right clicking it and selecting the 'Extract' option
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="osTicket Installation php 7 3 8 being extracted by clicking on PHP folder" src="https://github.com/user-attachments/assets/66608b9c-57a4-49ff-b781-c94e6a3b81d6" />

## 5. Then I browse and select the PHP folder that was recently created by me

<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="osTicket Installation once PHP folder is found in C drive and selected then click Extract button" src="https://github.com/user-attachments/assets/99ceca0c-f477-4979-a4ae-892bdd18bc79" />




## <h7>Install Visual C++ Redistributable</h7> 

## 1. I went back into my osTicket-Installation Folder again and click 'VC_redist.x86.exe' to install the neccessary libraries as shown in image below:

<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Next Install VC redist 86x" src="https://github.com/user-attachments/assets/78cce297-230e-481c-aedd-b8e5869e206e" />

>[!NOTE] Understand that osTicket relies on URL rewriting for proper navigation and functionality. 

## 2. In The Visual C++ below click I checked box I 'agree to licensing terms and conditions' as shown in image below:

<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="VC redist 86x C++ click the Licensing Box and click Install" src="https://github.com/user-attachments/assets/766021a2-8d52-4e68-8ac8-a96450601bce" />

## 3. I understand that this file that I'm installing will fully load and install and once it does then click 'Close' as shown in the image below:

<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="VC redist C++ once installed fully the click &#39;Close&#39; button" src="https://github.com/user-attachments/assets/d4d8e6cb-c5f0-402c-a737-139f8b46e876" />

  


## <h6>Next Process: Install and Configure MySQL Server</h6>
## 1. In this process for this discrepancy  I went back to my "osTicket-Installation-File folder that unzip and inside I located 'mysql-5.5.62-win32.msi' and initiate installation and begin the installation process.

  <details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>
   <img width="321" height="467" alt="Install mysql 5 5 62 for osTicket database" src="https://github.com/user-attachments/assets/eae6e8ee-f9fe-4a6b-9f3f-47b72672af32" />

   ## 2. I 'Accept the Licensing and Terms' for mysql-5.5.62
   
   <details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>
   
   
   <img width="321" height="467" alt="mysql 5 5 62 click licensing box then click next" src="https://github.com/user-attachments/assets/e295a21d-1623-4124-a7cb-c192de80dbac" />


   
## 3. I then Select 'Typical' Installation shown in the image below:
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="mysql server data base click &#39;Typical&#39;" src="https://github.com/user-attachments/assets/1906905c-86fe-4084-ad7d-411cca8a3533" />





## 4. I click Install and launch the MySQL Configuration Wizard shown in image below:
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="mysql server database click Install button" src="https://github.com/user-attachments/assets/3aceda39-14e4-4777-90eb-cba4b5c265cc" />


## 5. Configuration Wizard: Select Standard Configuration Options
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="To launch mysql database configuration click the &#39;Standard&#39; option" src="https://github.com/user-attachments/assets/cba6c1d8-15c1-457d-874a-ee1c0b857916" />


## 6. I Continue selecting Next as leaving everything else 'as is' until I had reach the Modify Security Settings screen and set both the username and password to 'root'. Then Finish the setup.
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="mysql database typing in &#39;root&#39; but not good for business environment but leave everything as is" src="https://github.com/user-attachments/assets/2e2eb850-2c03-4442-974e-f5ff4ca42edd" />

   
 After installation completes, launch the MySQL Configuration Wizard


## 7. I proceed by selecting 'Next' and clicking 'Execute' button that shown in the image below:
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="after typing &#39;root&#39; for password in mysql for configuration process then click the&#39;Execute&#39; button" src="https://github.com/user-attachments/assets/c807c715-fbe7-48e7-be26-7fb9dca7b9ab" />


## 8. I Finish the configuration on my "mysql 5.5.62' file
<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="mysql 5 5 62 once everything is checked off in processing configuration then click &#39;Finish&#39; button" src="https://github.com/user-attachments/assets/7a29c1bf-559c-4496-8e74-47b228e691b7" />


MySQL serves is the database backend for osTicket, storing tickets, user information, and all system-related data.


<details><summary>See screenshots</summary>

<img src="images/Step 2b.png" width="60%">
</details>



### <h8>Next Process: REGISTER PHP WITH IIS (Internet Information Services)</h8>
- How To Open IIS Manager 
- How To Register PHP 
- How To Restart IIS 


## 1. In my virtual desktop I search for IIS which is "Internet Information Services" and right-click, and then select Run as Administrator.
<details><summary>See screenshot</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="For IIS Mnager click the &#39;Run as Admin&#39; button" src="https://github.com/user-attachments/assets/b3413e9d-2e7d-4131-828c-12f2734c3eef" />



## 2. Once I got to my IIS Manager home page I then double-click on the PHP Manager "Register New PHP Version" which is shown in my image below:
<details><summary>See screenshot 1</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Once IIS Manager is open as Admin the register the PHP Manager by clicking it " src="https://github.com/user-attachments/assets/f3dd183f-f53d-4f57-8ce4-8ac42b375d70" />

<details><summary>See screenshot 2</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="944" height="497" alt="Once double clicking the PHP Manager inside IIS Manager then click &#39;Register new PHP version&#39;" src="https://github.com/user-attachments/assets/472c316c-8505-44e6-9a7a-98b082646eb8" />


## 3. browse to C: drive to find PHP to select 'php-cgi.exe'.
<details><summary>See screenshot</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="Extracting php cgi" src="https://github.com/user-attachments/assets/7e54ce29-544a-458a-be09-05832091372f" />


## 4. Make sure the php-cgi.exe is fully 'Installed'
<details><summary>See screenshot</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="After finding php cgi exe in the PHP folder and then click OK button now is has registered PHP and we back to PHP setup" src="https://github.com/user-attachments/assets/1ee2d9ef-ce46-4afe-95fd-9db36bddc373" />


## 5. Stop the IIS Manager in order to apply the changes.
<details><summary>See screenshot</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Reload IIS 1 click STOP " src="https://github.com/user-attachments/assets/80168d66-fd57-47be-b851-2072ad58e4c6" />

## 6. Start the IIS Manager in order to apply the changes.
<details><summary>See screenshot</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="To Reload IIS 2 the click &#39;START&#39; againg" src="https://github.com/user-attachments/assets/cdb1324c-5d4b-433b-90df-66f7a9462a35" />





### <h9>Next Process: ENABLE OSTICKET FEATURES AND ASSIGN CONFIG PERMISSIONS</h9>
* How To Extract osTicket Files
* How To Configure File Permissions

   ## 1. Extract 'osTicket-v1.15.8.zip' by right clicking the file
<details><summary>See screenshot 1</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="osTicket Installation Folder right click v1 15 8 to Extract it" src="https://github.com/user-attachments/assets/9c312ccb-ec6b-439d-84dc-4f05d0af11ca" />

<details><summary>See screenshot 2</summary>

<img src="images/Step 2b.png" width="60%">
</details>

 
  <img width="321" height="467" alt="Once you get to the Extract Compressed box the lean it at v1 15 8 and below click &#39;Extract&#39; button" src="https://github.com/user-attachments/assets/2f89971e-58c3-4cfa-9af7-a49958908415" />
  
<details><summary>See screenshot 3</summary>

<img src="images/Step 2b.png" width="60%">
</details>
 <img width="321" height="467" alt="Now osTicket v1 15 8 is fully unzip or Extracted and made another folder uptop" src="https://github.com/user-attachments/assets/4bac78f8-92cb-49e2-9981-277ddc0061da" />


  ## 2. Then copy the 'upload' folder to'C:\inetpub\wwwroot', renaming it to 'osTicket'.
  
  <details><summary>See screenshot 1</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="Copy the &#39;upload&#39; folder from new osTicket v1 15 8 into the &#39;wwwroot&#39; folder" src="https://github.com/user-attachments/assets/92e4419b-591c-4f95-8a6d-8ae7340ecc48" />


   <details><summary>See screenshot 2</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Loading the &#39;upload&#39; folder into wwwroot folder" src="https://github.com/user-attachments/assets/561e1fcc-9f53-4811-ad7a-b7c8d8f46b2f" />


<details><summary>See screenshot 3</summary>

<img src="images/Step 2b.png" width="60%">
</details>
  
  <img width="321" height="467" alt="Fully Finished on pasting &#39;upload&#39; folder into wwwroot" src="https://github.com/user-attachments/assets/46407404-81ca-43ce-8ffd-e4f3c97486eb" />

  <details><summary>See screenshot 4</summary>

<img src="images/Step 2b.png" width="60%">
</details>

  <img width="321" height="467" alt="Rename the &#39;upload&#39; folder inside wwwroot and call it &#39;osTicket&#39;" src="https://github.com/user-attachments/assets/5af4f2ee-782b-486f-b3a8-8bcb5435976d" />



  
  ## 3. In IIS Manager, enable the following extension
 -'php_imap.dll'
 -'php_intl.dll'
 -'php_opcache.dll'
 <details><summary>See screenshot 1</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="After leaving osTicket localhost and clicking PHP Manager click &#39;Enable or disable an extension&#39;" src="https://github.com/user-attachments/assets/2a06b1be-8251-45af-a6f5-232ea1121e1a" />

<details><summary>See screenshot 2</summary>

<img src="images/Step 2b.png" width="60%">
</details>

 
 <img width="321" height="467" alt="For Extension put enable mode for imap" src="https://github.com/user-attachments/assets/3199a0aa-0f18-41eb-a1b5-9e59b9a63887" />

  <details><summary>See screenshot 3</summary>

<img src="images/Step 2b.png" width="60%">
</details>

 <img width="321" height="467" alt="For Extension intl put enable mode" src="https://github.com/user-attachments/assets/c9d9de6d-3ca2-4345-8fa8-50ad1b196ab1" />

 <details><summary>See screenshot 4</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="For Extension opcache put enable mode" src="https://github.com/user-attachments/assets/689cd4e3-aa64-47aa-9e02-a3fe6e5f6463" />

Now all PHP Extensions are now 'ENABLED'.
 <details><summary>See screenshot 5</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="After leaving osTicket localhost and clicking PHP Manager click &#39;Enable or disable an extension&#39;" src="https://github.com/user-attachments/assets/eab54ab3-e663-4026-b1aa-297d023af59c" />

 <details><summary>See screenshot 6</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="The localhost osTicket new refresh page" src="https://github.com/user-attachments/assets/adba184c-9713-41f4-979a-1b0ae3f975af" />



 
 

  ## <h4>Next Process and Procedures For 'ost-sampleconfig.php': 
  
  ## 1. Rename 'ost-sampleconfig.php' to 'ost-config.php',  option and set permissions for "Everyone" temporarily.</h4>
  <details><summary>See screenshot 1</summary>

<img src="images/Step 2b.png" width="60%">
</details>
  <img width="321" height="467" alt="Once in the &#39;INCLUDE&#39; folder rename ost sample to ost config" src="https://github.com/user-attachments/assets/b0dfd33f-ae3e-4226-9c3b-c6bd506f16e2" />

  
## 2. I then right-click to go to and click 'Properties' option
  
 <details><summary>See screenshot 2</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="ost-sampleconfig to new name ost-config" src="https://github.com/user-attachments/assets/895e6107-20bf-4295-aaaa-050ad43d7690" />


## 3. From there I click on the 'Security' tab in my 'ost-config.php' which is shown in my below image:
 <details><summary>See screenshot 3</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Right click ost config and select Properties and click the Security tab then click &#39;Advance&#39;" src="https://github.com/user-attachments/assets/341bf16e-a050-42a6-b1a7-ba1e68dff56d" />

## 4. I then from there clicked the 'Advanced' button and also I click the button that said 'disable inheritance' on the left which is shown in the image below:

 <details><summary>See screenshot 4</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="For ost config after going into Properties and clicking &#39;Security&#39; tab and clicking the &#39;Advanced&#39; button then click on the &#39;Disable inheritance&#39;" src="https://github.com/user-attachments/assets/3bebe81d-e59c-4651-b25d-866b168c45f4" />

## 5. I then clicked on the second to feature option 'Remove all inherited permission from the object' so it can remove the old permission it orginally had and so i can make new permissions.

<details><summary>See screenshot 5</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="for ost config once clicking the &#39;Advanced&#39; button and then click &#39;disable inheritances&#39; and click option to REMOVE inherit permission" src="https://github.com/user-attachments/assets/50d2e8e0-a67f-4ed2-82ad-317f180bf3e8" />


## 6. From here the next step I did was click the "Add" button once i cleared out the old permissions from above.
<details><summary>See screenshot 6</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Now there no permissions and click the &#39;Add&#39; button to add new permissions" src="https://github.com/user-attachments/assets/1eef9cb9-de64-4274-b8f6-6966fdc0d5fd" />

## 7. From there a new page will open to select a new 'Principal' where I clicked left from about that is shown in image below:

<details><summary>See screenshot 7</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="ost config permission entry box click &#39;Select a principal&#39;" src="https://github.com/user-attachments/assets/4350a50d-1bec-4158-91f2-05233687295d" />

## 8. From that step what happened was my 'Select User or Group" box popped up and for project purposes to give an example and to make everything configured correctly I choosed to type and give permissions privilege to 'EVERYONE" which the word I use to type in the box.

<details><summary>See screenshot 8</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Permission Entry ost config type Everyone with understanding it not good to do in real life because security reasons" src="https://github.com/user-attachments/assets/0b34360d-fcdf-4bc1-940a-b27cb7166664" />

## 9. Next step I then click the option for 'EVERYONE' to get 'FULL CONTROL' option feature for the php configuration file in the 'INCLUDE' folder.

<details><summary>See screenshot 9</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="In Permission Entry ost config click &#39;Full Control&#39; box then click OK" src="https://github.com/user-attachments/assets/cd48e879-e005-4103-b0ef-f488ff59117d" />

## 10. After that I then click the 'Apply' button to apply the changes.

<details><summary>See screenshot 10</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="Click Apply from ost config Advanced Security Settings" src="https://github.com/user-attachments/assets/5ce23612-4e1b-4a4e-80f6-ce7490f3e765" />


## 11. Next step I did was click the 'OK' button as shown in image below:

<details><summary>See screenshot 11</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Then for ost config after clicking &#39;Apply&#39; the click the OK button" src="https://github.com/user-attachments/assets/87dc4149-cb2d-4c58-87a9-9a24779aaed9" />


[!Important VERY TO NOTE]: This is insecure and should be restricted in real production environments. Assigning 'Everyone' permissions to ost-config.php is insecure because it allows unrestricted access to a sensitive configuration file. This is done temporarily in this project to avoid installation issues; permissions should be restricted after setup in real business environments.



## 4. Now go back IIS Manager to reload it by restarting the web server again, stop and start instructions and here are my images below:
<details><summary>See screenshot 1</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="After leaving wwwroot folder comeback IIS Manager to reload 1 click &#39;STOP&#39; button" src="https://github.com/user-attachments/assets/982e22e0-e0a5-4e50-8540-d52806340723" />

<details><summary>See screenshot 2</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="After Leaving wwwroot folder comeback to IIS Manager 2 for to Reload and then &#39;START&#39; again" src="https://github.com/user-attachments/assets/2b0da0df-9320-4416-a205-ffa03ceb1ca5" />





## 5. Then minimize IIS Manager and Now in your web browser, navigate to 
 http://localhost/osTicket/scp/login.php

 <details><summary>See screenshot 1</summary>

<img src="images/Step 2b.png" width="60%">
</details>
 
 <img width="321" height="467" alt="The localhost osTicket new refresh page" src="https://github.com/user-attachments/assets/46ec7d6e-132e-4251-a40a-200f102b2a9a" />



<details><summary>See screenshot 2</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="After giving new permission to ost config file then hop back over to osTicket localhost and below click the &#39;Continue&#39; button" src="https://github.com/user-attachments/assets/60b31b71-0e3e-4bb0-9c63-215fcacace33" />




### <h10>Net Process:Setup Administrator Credentials For osTicket Helpdesk Browser</h10>
- Name Helpdesk
- Passwords
- Default email (receives email from customers)
- Everyday used Emails
 ## 1. Scroll down and click the 'Continue' button from the local host osTicket from image below:
  
  <details><summary>See screenshot 1</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="After giving new permission to ost config file then hop back over to osTicket localhost and below click the &#39;Continue&#39; button" src="https://github.com/user-attachments/assets/66e91b5e-0c43-429b-a59e-e67d6c6856d4" />

  ## 2. Type into the System setting Fields as shown in my image below:

  <details><summary>See screenshot 2</summary>

<img src="images/Step 2b.png" width="60%">
</details>

  <img width="321" height="467" alt="Typing into osTicket Fields before Installing" src="https://github.com/user-attachments/assets/6b7369b0-2459-4aaf-bf41-39e7a08bfcef" />

  ## 3.  I was able to filling in the fields that was relatable to Heidi

   <details><summary>See screenshot 3</summary>

<img src="images/Step 2b.png" width="60%">
</details>

  
<img width="321" height="467" alt="Typing out Fields for Heidi before Installing" src="https://github.com/user-attachments/assets/12eba346-dc53-417e-994a-f4bdd96c7d1b" />



### <h11> Next Procedure: CONFIGURATE and INSTALL HEIDISQL for osTicket Installation Credentials</h11>

Before we select Install Now, we will need to configure our SQL and create the database and connection that osTicket will use.
- Install HeidiSQL: 
- Create Database: 
- Include osTicket setup, select Continue >> near the bottom. 
- osTicket System Settings 
- In Admin User Field 
- Back osTicket in the installation folder, find <code>HeidiSQL_12.3.0.6589_Setup.exe</code>, and install it with all default settings, and select Finish to launch HeidiSQL.
- Navigating Session Manager window
- Recircle back to Heidi database server
- 1. Continue Installation: Navigate to 'https://localhost/osticket/setup/'
Back in the web browser, we will continue the osTicket setup. Enter the following
- MySQL Database Settings: 'osTicket'
- MySQL Username: 'root'
- MySQL Password: 'root'
- Complete Installation: "Select Install Now" button.


 Install 'HeidiSQL_12.3.0.6589_Setup.exe' with default settings.
 Connect using 'root' as the password, create a database named 'osTicket'.
 The osTicket setup, select Continue >> near the bottom.
 In System Settings, enter the help desk name and default email.
  In Admin User, enter admin name and admin email address, for username and password, we will set it to VBAdminuser and <code>Password2</code>.
 find <code>HeidiSQL_12.3.0.6589_Setup.exe</code>, and install it with all default settings, and select Finish to launch HeidiSQL.
Select Skip, in this Session Manager window, Select +New, and type <code>root</code> for the password here, and select Open.
 Recircle back to Heidi database server Right-click the Unnamed session, and select Create new, and select Database. Enter for Name: 'osTicket' (no space and capital T), and select OK.Run 
 
 Select Skip, in this Session Manager window, Select +New, and type <code>root</code> for the password here, and select Open.
 Right-click the Unnamed session, and select Create new, and select Database. Enter for Name: osTicket (no space and capital T), and select OK.Run  

## Below Here are the procedures and  I used to setup my Heidi Installation the programs to signup and setup osTicket Signup:
<details><summary>See screenshot 1</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="Typing out in the Fields for osTicket before Installing" src="https://github.com/user-attachments/assets/3e0b8436-5d7b-472f-9e8d-1031db6a94d1" />

## 2. I went to my unzip "osTicket-Installation-File" on my desktop and went inside folder and double-clicked on the HeidiSQL and accepted the Licensing in the image shown below:

<details><summary>See screenshot 2</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="466" height="346" alt="after getting this from desktop osTickect installation and accepting the licnese for Heidi click Next button" src="https://github.com/user-attachments/assets/4c43caf4-bd6a-4f05-823d-25a2d2d8ac85" />

## 3. I pressed forward and installed Heidi menu bar shown in my image below:
<details><summary>See screenshot 3</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="Heidi Menus Bar click &#39;Next&#39; button" src="https://github.com/user-attachments/assets/a7f6be04-af06-4f15-ae2e-16083892ade3" />

## 4. I made sure all 'Additional Task' was checked box and clicked next which is shown in the image below that I created a screenshot for.

<details><summary>See screenshot 4</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="Heidi leave everything as is and click &#39;Next&#39; button" src="https://github.com/user-attachments/assets/12dd90ba-ef42-49f5-9fd4-073a193b8afb" />



## 5. I finally then installed the Heidi SQL database for osTicketing system shown in my other image below:

<details><summary>See screenshot 5</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="The Final Heidi Installing Now" src="https://github.com/user-attachments/assets/f624230e-350c-4dfb-b026-eb433ef58975" />

## 6. I finally came to a finish line for my Heidi SQL Wizard that was completed and I clicked below the 'Finish' button shown on the image below:

<details><summary>See screenshot 6</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Final Final click the &#39;Finish&#39; button for Heidi" src="https://github.com/user-attachments/assets/190b1503-d9f8-4496-bb26-c07393850ad3" />

## 7. Then instead of checking update for my HEIDI SQL I then clicked the 'skip' button

<details><summary>See screenshot 7</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="Check for Heidi Updates click the &#39;Skip&#39; button" src="https://github.com/user-attachments/assets/ae038218-2498-4e21-a469-5051299b09b3" />

## 8. I then opened up my Heidi SQL Session Manager and click the 'New' button which is shown in image below:

<details><summary>See screenshot 8</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="Heidi Opens up with Session Manager box now below on Left click on New button" src="https://github.com/user-attachments/assets/b37e31c6-eae1-4951-902a-77b7552bb583" />

## 9. In the Session Manager for Heidi SQL I type in my original password that I created under mysql server which was 'root' and where I have it in the image below:

<details><summary>See screenshot 9</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="Heidi session type &#39;root&#39; for Password field to as well which was set up in mysql 5 5 62 and click &#39;Open&#39;" src="https://github.com/user-attachments/assets/6db4c306-5067-41fc-a32d-df8746903f45" />

# 10. I then created a database for 'osTicket' by right-clicking 'unnarmed' dolphin icon and then selecting 'create new', the selecting 'database' and a

<details><summary>See screenshot 10</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="For Heidi now a click is open to osTicket database" src="https://github.com/user-attachments/assets/d5f9bf23-c26d-4d27-a5e1-7b6a3a028baa" />

## 11. I then created a database for 'osTicket' by right-clicking 'unnarmed' dolphin icon shown in the image below:

<details><summary>See screenshot 11</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Inside Heidi database Host page right click &#39;unarmed&#39; then click &#39;create new&#39; then click &#39;database&#39;" src="https://github.com/user-attachments/assets/99101f73-75cf-4089-8db6-af3e6e88825d" />


## 12. from there I select the option 'create new'
<details><summary>See screenshot 12</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Heidi osTicket database it will eventually create things inside of there" src="https://github.com/user-attachments/assets/58e282da-213f-4b25-9921-fd60f22b99de" />


<details><summary>See screenshot 13</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="once right clicking &#39;unarmend&#39; and create new database now call it &#39;osTicket&#39;" src="https://github.com/user-attachments/assets/cad37cf4-03ac-4ce3-9060-22a0ab74ae8e" />

>[!IMPORTANT NOTE] In this image you would need to type in the side the field 'osTicket' and like mentioned before with an captital 'T' and then click OK.


 
## <h13>VERIFY INSTALLTION AND FUNCTIONAILTY</h113>
Congratulations, refer to the screenshots to ensure functionality!
- Admin Login: http://localhost/osTicket/scp/login.php
- For End User to create tickets: http://localhost/osTicket/


<details><summary>See screenshot 1</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="Congratulations osTicket finally and fully INSTALLED" src="https://github.com/user-attachments/assets/d0a809c4-28d4-4c10-aa5c-1973c8688e2c" />

## 2.This image is the Administrative Login for Admins and Technical Support Teams right now it authenticating
<details><summary>See screenshot 2</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="osTicket 1st Login Verification for me the Admin" src="https://github.com/user-attachments/assets/3e5d82c2-940d-4dc6-8a26-c2866026dfd2" />

## 3.This image is dealing with finally getting inside of osTicketing system
<details><summary>See screenshot 3</summary>

<img src="images/Step 2b.png" width="60%">
</details>
<img width="321" height="467" alt="Finally login and inside osTicketing system " src="https://github.com/user-attachments/assets/15d76ef9-a59c-4327-9384-5e0986725f48" />

## 4. This image below is osTicket End User Page where Users can submit tickets on any technical issues or inquiries they might have
<details><summary>See screenshot 4</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="osTicket End User page setup for Users to submit tickets" src="https://github.com/user-attachments/assets/9a1dab15-6c9e-4a75-b081-98c7e76754c4" />

<details><summary>See screenshot 5</summary>

<img src="images/Step 2b.png" width="60%">
</details>


<img width="321" height="467" alt="After Fully INSTALLING osTicket go back to Heidi database and right click &#39;osticket&#39; and click refresh option" src="https://github.com/user-attachments/assets/d4928a44-1f7b-4978-8ae5-03aa1b3516d7" />

<details><summary>See screenshot 6</summary>

<img src="images/Step 2b.png" width="60%">
</details>

<img width="321" height="467" alt="Inside Heidi osticket after refreshing you see the fields and function, department BUILT into osTicket" src="https://github.com/user-attachments/assets/f23c3abd-7c5f-43c6-9111-38b54690f17d" />

>[!NOTE]: As you look at the image above these are functionality on the backend of osTicketing systems that's already built in that I built on my own.





















  















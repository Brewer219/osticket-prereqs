<p img width="1356" alt="osTicket" src="images/osTicket Logo.png" />
</p>


<h1>osTicket: Installation</h1>
<p>
This project outlines the process of installing a self-hosted osTicket help desk system on Windows. It marks the first installment of a three-part series that will cover installation, configuration, and ticket lifecycle management. The emphasis is on deploying osTicket using modular infrastructure components instead of relying on a single bundled installer. This approach highlights the preparation and integration of the web server, scripting runtime, and database necessary for the application. Establishing this foundational setup creates a robust environment for future projects, which will delve into system configuration and practical ticket workflows.</p>

<h2>2. Technologies Used</h2>

<p align="left">
<img src="https://skillicons.dev/icons?i=azure,windows,php,mysql" />&nbsp;&nbsp;<img src="images/osticket-icon-dark.png" width="48"></p>

 - Internet Information Services (IIS)
 - PHP
 - MySQL
 - osTicket

<h2>3. Operating Systems</h2>

- Windows 10 Enterprise 22H2

<h2>4. High-Level Deployment Overview</h2>

- Prepare the Windows server by enabling required web server roles and features.
- Install and configure the PHP runtime and supporting dependencies.
- Deploy and configure the database backend for osTicket.
- Integrate all components and complete the osTicket web-based setup.

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
Remote Desktop Connect(RDP) to the newly created VM, download the osTicket-Installation-Files.zip from the repo and unzip the whole folder unto your VM desktop. Search the start menu for "Turn Windows features on or off". In the pop-up find Internet Information Services and mark the checkbox. Expand World Wide Web > Expand Application Development Features, find CGI and mark the checkbox, and select OK and wait for features to be installed.

<details><summary>See screenshots</summary>
<img src="images/Step 2a.PNG" width="40%" >
</details> 

> [!NOTE]
> Internet Information Services (IIS) is the web server that will host the osTicket application.


<h3>2. INSTALL PHP MANAGER AND PREREQUISITES</h3>
A. In our Installation folder, find the PHP Manager Installer (PHPManagerForIIS_V1.5.0.msi) and install it.

> [!NOTE]
> osTicket is a PHP-based application, and PHP Manager allows IIS to run and manage PHP files so the application functions properly. Installing PHP and supporting runtime dependencies, ensuring version compatibility with osTicket.

B. In our Installation folder, find the Rewrite Module (rewrite_amd64_en-US.msi) and install it.

> [!NOTE]
> osTicket uses rewritten URLs to work correctly, and the Rewrite module allows IIS to handle those requests properly.

C. On the C: drive, create a new folder named <code>PHP</code>.  From our installation folder, unzip or extract the contents of <code>php-7.3.8-nts-Win32-VC15-x86.zip</code> into the C:\PHP folder. The extracted files contain the actual PHP runtime that IIS will use, while the PHP Manager we installed is used to configure and manage it.


D. In our installaion folder, find VC_redist.x86.exe and install. We need to install the Visual C++ Redistributable because PHP depends on these runtime libraries to run correctly on Windows.


E. In our installation folder, find <code>mysql-5.5.62-win32.msi</code>, and install it. MySQL is installed to provide the database where osTicket stores all tickets, users, and system data. Select Typical > Install, and then Launch Configuration Wizard after installation. Choose Standard Configuration, then select Next until reaching the Modify Security Settings screen. Enter <code>root</code> for both the username and password fields, then continue by selecting Next and finally Execute and Finish.

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




# osticket-prereqs
![image alt](https://github.com/Brewer219/osticket-prereqs/blob/d185f11c3e05863c51e793406859ad1de047e0c3/downloaded%20osTicket%20on%20Virtual%20Machine.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/93321c5cbccc8568b1fc3f5f61f4dcded25c4b40/Inside%20osTicket%20Folder.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/ab2ecb6cf64c106ea4952caa31ed56e916b37645/Step%201%20of%20Installing%20IIS.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/88ee3a654eb31a9c461e106d93cb674b077d8474/Step%202%20of%20Installing%20IIS.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/91bef29f29ae71f353cb4b44f0133d06f00492f6/Step%203%20of%20Installing%20IIS.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/304609fa608a0641d3009b3079f0bf7cfbbebc04/Step%204%20of%20Installing%20IIS.png) 

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/34c06845ebebf66cbaf1e575d3c8f730f14ef77a/Step%205%20of%20Installing%20IIS.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/054e69253aa87b1f5910724ed847d27b52034113/Step%206%20of%20Finishing%20IIS%20Web%20page.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/bbcfd4f4c06ac9fcdff791a58911657b59272902/Step%207%20Download%20PHPManagerIIS_v1.5.0.msi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/dfb512f180493ea058191015df555d52b204f750/Installing%20Rewrite%20file.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/fc7a4b55879008dda3efab8b373adb1aba640691/Step1%20Downloading%20Rewrite%20File.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/bc43f2bd45ee9264f15d44749d4dac9c8b11ebd2/Finished%20Installed%20Rewrite%20File.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/6a91884a41db597844247307a113288edfe49090/This%20PC%2C%20C%3B.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/32f0f746f88ddb929ba23d9e4f97aeab69230b03/CopyPaste%20PHP%20folder%20inside%20C%3B.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/5d5a55295cd7e40bf337d6bcc6c102eee9df3d3b/Extract%20unzip%20file%207.3.8.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/72ad0007b5cbd043437c6104558363bfbbbbf9c7/php%207.3.8%20right%20click%20for%20Properties.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/1eb8441f98e06151aaa0d08f616222f60c3d5764/Extract%20php%207.3.8.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/182a81ad01e492f78c4f6a68cc1145da6aaae20e/Extract%20C%3BPHP%20folder.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/445301d8c7433e0969496384e499bc259a0362db/Click%20and%20Download%20on%20VC_redist.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/fa7b99b32c417d1bf3e7add4ad822ad0ded6b64b/Install%20VC_redist.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/4bcfbcd31005c0adae5ce57b62cc782c96c25b73/Step%201%20SQLsever%205.5.62.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/b9794c1c4bfc593fc510d54bfd9a02fbc70d9baa/Step%202%20SQLsever%205.5.62.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/0f8ec0e66362e5e747a9c0cd0d9689c6829a7569/Step%203%20MySQL%20sever%205.5.62.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/a2d8f10228cb901d6c825da025b2dcadc1a3bf16/Step%204%20MySQL%20server%205.5.62.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/2101739d9441b2159d566486428890f988021b43/Step%206%20MySQL%20server%205.5.62.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/e0b450cf3c0c64e86327835ea3a1d49e3eae2474/Step%205%20MySQL%20server%205.5.62.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/8140ed2ee82841b86fbc743d6aff35fea9aa4cb0/Step%209%20MySQL%20sever%205.5.62.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/118c81c7c35715e39fcd3e9401f7ee871cd84af5/Step%201%20Open%20IIS.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/8451322d4c9707c769a61f21646da9a22efb1b20/Step%202%20%20click%20PHP%20Manager.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/f517626097909955310d47059d195178c0e7f1b8/Step%203%20Register%20PHP.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/eddab009ecc0fac084ebfaa902d7b0154b7ac55d/Step%204%20click%20php%20binary.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/499ed3aa51af90ee6d97313a20e02d8f7a2bd4e1/Step%205%20complete%20php.cgi%20binary.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/4be1f1ced99755e741fc3a7bff7784df151271b8/Step%206%20Finished%20php.cgi%20binagry.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/22c914ee89cb7c43f3ba3ad273f537c74797424b/Step%207%20php%20binary%20clicking%20the%20STOP%20button.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/f0b88b4bf78e56fcc20997cf54aa76ad01ba1bf2/Step%208%20php%20binary%20clicking%20the%20START%20button.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/ddd689f333ab084c7a944a8cf7f5755d62281074/Step%209%20php%20binary%20RESTART.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/aa4f92980ce63cb4b2263a2c177437cd4515f4cb/Step%201%20Install%20osTicket%20v1.15.8.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/29ebad5ce147192be6f7ed574303bf4c8e1b403a/Step%202%20Extract%20v1.15.8.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/153350082f198221ba206c68e41b4cb0a63fae70/Step%203%20osTicket%20v1.15.8%20inside%20of%20the%20folder.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/9a997737bea86b2d33577748a2d3c82a27f2e1bb/Step%204%20extract%20v1.15.8%20double%20file%20created.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/f3f80bb50e09fd40c06d0b4426049eab1a05269d/Step%205%20osTicket%20v1.15.8.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/2ab9d9e416e5c2ef3ce932db0f48224f90cc0f03/Step%206%20v1.15.8%20osTicket.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/823f06f46abe39d6dd65896b1d218c978a3163ce/Step%207%20v1.15.8%20copying%20upload%20folder%20into%20wwwroot.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/d4dc0503811e93acb288f1183dc03a5d885c7c41/Step%208%20v1.15.8%20finishing%20with%20copy%20upload%20folder%20into%20wwwroot.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/9d1148f4b32dbf058f63fdb03165f1bba995eda8/Step%209%20v1.15.8%20rename%20osTicket%20inside%20wwwroot.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/3600026ad4c83c43727a3003d78fcee6977c78da/Step%2010%20v1.15.8%20click%20STOP%20button.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/dc03ca245c3337388175d3bd947cf76de12fbed8/Step%2011%20v1.15.8%20osTicket%20RESTART%20button%20Hit.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/0fc882486861d62236f8050e2b5eb78102e57f24/Step%2012%20v1.15.8%20click%20SITES.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/e00c5c6d417163f258ead8e863de6a8ed77b699d/Step%2013%20v1.15.8%20click%20DEFAULT.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/63ce53e40c9a33f088920afd5ac99f1f9d212cec/Step%2014%20v1.15.8%20click%20osTICKET.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/cb7d3d11961f7b7bc9f5c07171a3d546d52479b8/Step%2015%20v1.15.8%20click%20Browse%2080.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/2064ff41154eafe25c5b0d6876a5f5d2ff2fe26b/Step%2016%20v1.15.8%20after%20clicking%20Browse%2080.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/bc4de0c7cf9cb09e8634ef172a22806a3198f16c/Step%2017%20v1.15.8%20click.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/4c4d54f12b00400ca35cdf41c80afb71c169e84c/Step%2018%20v1.15.8%20PHP%20ext%201.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/12d70e0e259d2322372f7ae33e27115607db6354/Step%2019%20v1.15.8%20PHP%20ext%202.png

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/b1929f878dc9c8f68ca7c9607e6e68baab50c655/Step%2020%20v1.15.8%20PHP%20ext%203.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/5345e8a785b584ac2a268d1ef0ed243a2673be34/Step%204%20get%20inside%20include%20folder.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/f108a7d41a23cf4cdaf40da97afb34c8b89fc11b/Step%205%20ost-.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/8b18aefd9263cd8cdd8cc15ac23b6fab95404f07/Step%206%20ost-.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/4e778bfe48d2775e06aed6022a6311ba6cfd7e62/Step%207%20ost-%20Right%20click%20for%20properties.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/a0507b3d88554aed1e5c6091af1b5b5074cfe7e7/Step%208%20ost%20-%20click%20Security%20tab.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/894e93283b098dff5a0412bf7bb7dc61218ad4d3/Step%2010%20ost-%20Permission%20tab.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/e4458c92cf5f87021aa8b5f89914ddc9e45d2f2d/Step%2011%20ost-%20add%20new%20permission.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/4aabfe5651dbb42d4679f61b9d4c52b0701e0e98/Step%2012%20ost-.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/cad4a606b57ac5a994f4dd72006dc78e34131f21/Step%2013%20ost-.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/c0409e0c086694e96ad98adc9691b8be4432d17b/Step%2014%20ost-.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/07b5b8729bf62ee7f42fd598dd65a9ba10f9f310/Step%2015%20ost-.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/596d2c5f5c50147d364387917987dfb79021df42/Step%2016%20ost-%20hit%20apply%20then%20okay.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/d9c584fbcf3b1b1915afb32d2eccefc57c056edb/Step%2017%20ost-.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/98ddce1a5bd86b787f6bce31e6c494bb54a258c6/Step%201%20click%20on%20Hedi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/28f6e42ce28c3f135285df1a4b197aeaaf089fe9/Step%202%20Hedi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/d57cc42d95c6bf7fdd60fad1ba33582f0a3ac450/Step%203Hedi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/b7191064e492a8f1d64eb922ba8b5c1fbc0f6f12/Step%204%20Hedi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/18ad7d1b6d4eda936b3a4af18af33cb03cc244c7/Step%206%20Hedi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/e275ff6e99a89209ff0e85458e1d303ccef0e569/Step%207%20Hedi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/606098ccb5ffe5613b1174c203638f4a629fa388/Step%208%20Hedi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/1840b6a46dce33f4a86494d26c6d0b7de55e4079/Step%209%20Hedi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/4b6d013b978d76c9283d91668f842561fc7f2de3/Step%2010%20Hedi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/12e955d6073b13795ca86ac8a5b109c21f7877f8/Step%2011%20Hedi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/6b45ebdfcda8d7022070dd2d1ae6625abf0b4643/Step%2012%20Hedi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/52d48fdc321ac6febf46ea39731a88024f654923/Step%2015%20Hedi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/d2e7e78e54098a7add5b5f89efd2d9dd49ff6c46/Step%2016%20Hedi.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/1a1da4ce8b3ebd0721036bab0c39ff954a56e453/Step%2017%20Hedi%20osTicket%20Install%20Admin.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/f1ba99325f9c7181b75b908958cf53c26f7f1584/Step%202%20Admin%20osTicket%20refresh.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/70ac61493e3a32ef88549ee4157b4aeacfdb2280/Step%203%20Admin%20Staff%20Control.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/af9f528af2f1802639de7533519d8fe9ebf1abce/Step%204%20Admin%20login%20cred.png)

![image atl](https://github.com/Brewer219/osticket-prereqs/blob/e8e446347934dddad2748646d06f4e62423f7c45/Finished%20Logged%20into%20osTicket%20system%20part%203.png)

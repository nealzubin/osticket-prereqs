<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)(coming soon)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Enable IIS
- Install Web platform installer
- Install MySQL
- Install C++ Redistributable
- Configure Permissions and Install osTicket

<h2>Installation Steps</h2>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/62cc4a71-bbbf-47ae-ad2c-16e567e82081)

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/12ab1a6f-18a1-4c88-b2b3-bb91adae0f8d)



<p>
We will start creation of our Azure Resource Group and Virtual Machine. In the fictional hospital of CyberLake, we will create an osTicket system the various employees will be able to use to get IT help. Step 1 is going to www.portal.azure.com. From here, we will select the red boxed "resource groups" in the image above. After filling out the fields and naming our resource group, we will click "review+create" > "create". We are now moving on to creating our virtual machine. 
</p>
<br />


![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/7d5251dc-3489-400d-bd45-8688f29dbf10)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/12c04ff6-0421-4dbe-94d9-f79c23b8b9d6)


<p>
Once you click "virtual machines" and create VM from scratch > fill out the fields as listed below. Make sure the region of your VM is same as the region of your resource group. Once you fill out the fields listed in the screenshots below > click next for "Disks" > next for "Networking"
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/ba56c4bf-77d9-4480-b4f1-ab04d3bc33cd)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/92a8dda3-790a-48d2-bafe-864db1300e22)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/71e7418f-0e20-4e18-bb29-b4a0d47252c4)


![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/d12c7cde-d159-469f-a4d5-708d4461f5fb)


<p>
Once you are at the networking tab, we are going to allow azure to create our virtual network. This will also create a virtual subnet automatically. Finally, we will click "review+create" > "create"
</p>
<br />



<p>
Once we have created our VM's and RG, we are going to remote into our virtual machine and begin installing software. In order to get logged into our VM, we need to use remote desktop connection(windows) and microsoft remote desktop(MAC). We will type in the public IP address of our virtual machine to connect. 
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/5a3c1680-28d0-4bd0-a0d9-686455770c92)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/237206a7-01b7-45f5-8202-3aee9238f117)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/9a0d4145-04ce-4f84-8e2e-cc5d4c9378ac)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/9fd9dd81-6153-4015-aaed-7f5ffcfe5267)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/5926897a-d7de-4e8e-9375-47222851ba30)






<p>
Once we have connected to our VM, we will begin installation of the necessary prerequisites for osTicket.
</p>



<h2>Installation Steps</h2>

<p>
We start by enabling IIS(internet information services) in windows with CGI and common HTTP features. IIS is essentially a web server that allows your VM to serve up websites because osTicket runs out of a website. To do that, right click the start menu and click run. Type control panel > programs > Turn Windows features on or off
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/9a5686b2-ceed-4527-9673-23f816ac3707)



<p>
Next, we enable IIS by checking the box. After that, expand the IIS box by hitting the "+"
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/c972939c-af3c-42ab-bb11-69b7c91f88cb)


<p>
In the IIS dropdown, we want to navigate to Application Development Features > CGI. Check this box. 
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/68ef9cd0-6b7a-4fd1-beff-7b3eb618b8f9)


<p>
Collapse the Application Development Features menu and then open up the "Common HTTP features" menu. Make sure all of these are checked. Then click ok. 
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/d22c510e-fd2e-485e-b52a-5d47cc2d44fa)

<p>
We can confirm IIS was installed by opening up a web browser and typing in our loop address of 127.0.0.1 The screen will resemble the one below.  
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/d21fb14b-6048-4ab3-84b5-5327201a81af)



<p>
Next, we need to download a PHP Manager for IIS
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/974b1e7f-5415-4714-972f-62643c27c06a)


<p>
Now we download and install the IIS URL Rewrite Module
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/cffb97e8-965a-4825-b350-d5c82dee93ca)



<p>
Create the directory C:\PHP. This can be done in file explorer > C drive > New folder > rename to PHP
</p>


<p>
 Download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP
</p>



![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/95e0152e-499c-478f-8b8e-be8d1062fa54)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/8f8f44e1-b7f3-45d5-83af-bdd69df1199a)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/c89c357e-5393-48b1-af3c-fe2c08bad9b3)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/2b21928d-76b9-4a87-b758-be83b9f65bad)


<p>
 Download and install VC_redist.x86.exe.
</p>


![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/b60ea1c2-964a-482b-86e8-fb1c299e7893)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/8f48b688-7f07-4583-947d-8113f7dec5ec)



<p>
 Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) > Choose typical install > Standard Configuration > Install as Windows Service
 Select Modify Security Settings > Enter root password from before
</p>


![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/5dbb89d3-1b9b-4f9c-9217-037a68591b0e)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/e785e940-69e7-4294-9cdc-ee46a20b418f)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/4c7da104-04ba-4053-85c7-79e3cb743ca9)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/7fdd6aeb-9c04-4daa-b3a1-dceebd67ed83)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/965d7cae-9805-4613-9dd3-aa65f201d519)





<p>
Open IIS as administrator > Register PHP from within IIS > Reload IIS (Open IIS, Stop and Start the server)
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/2c5b94ea-76bf-47b6-b7da-b0e733b65c44)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/421885d5-67a8-4a41-afbc-d820411e2820)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/974ee1b0-ee29-4b34-879b-9a093f44c547)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/1ad8d915-8816-48e6-842d-1ef63098f170)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/5aedb19f-8a26-4ab1-963d-bb3952a91ab5)






<p>
Install osTicket v1.15.8 > Download osTicket from the Installation Files Folder > Extract and copy “upload” folder to c:\inetpub\wwwroot >
 Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
</p>



![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/2e716c2f-cca5-4662-adcb-65317d453b18)




<p>
Reload IIS (Open IIS, Stop and Start the server) > Go to sites -> Default -> osTicket(On the right, click “Browse *:80”) > 
Note that some extensions are not enabled
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/3133dfc8-a699-48b5-9c95-8d3971dcf6f9)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/459db672-32d5-4177-8895-dd9adc9005bf)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/e3e88230-550c-4ec4-9d61-41138ef03e83)



<p>
Go back to IIS, sites -> Default -> osTicket > Double-click PHP Manager > Click “Enable or disable an extension” 
 > Enable: php_imap.dll > Enable: php_intl.dll > Enable: php_opcache.dll
Refresh the osTicket site in your browse, observe the changes
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/62675bb7-6995-4171-be65-eb94b9d57418)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/19000756-a96f-44ad-96f1-ed27141bad5f)



<p>
Rename: ost-config.php > From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php > To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/5d25a443-2419-4661-9719-12c060379e12)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/ef198d41-07c4-4fed-8d95-8234d8d5373e)



<p>
Assign Permissions: ost-config.php > Disable inheritance -> Remove All > New Permissions -> Everyone -> All
</p>


![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/3a90fcc4-9b13-41e2-9af8-94b0bf78ef9d)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/5b3a10c1-7f6b-4e80-900e-58d9ab91d7d9)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/bdde349e-5899-444c-9be9-ff6167e59497)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/40249e6f-1064-4d8a-b937-a71283ec2d8f)


<p>
Continue Setting up osticket in the browser > Name Helpdesk and Default email (receives email from customers)
</p>

![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/d3bba7f4-7ce1-4fae-ad45-bd755e21230d)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/cc3d11cc-733a-43bd-b354-a6583301a399)



<p>
We know have to set up our database before continuing further with the installation. 
  download and install HeidiSQL > Open Heidi SQL > Create a new session, root/Password1 
 > Connect to the session > Create a database called “osTicket”
</p>


![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/ddbb2da7-cfe4-48dd-bd6f-f0bac54c62e8)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/097ca4c8-bc0e-4e9d-9ce4-546ac0d3454a)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/10686296-a119-4a60-a397-fe81879b0706)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/9c3d1f74-189c-447c-b3fb-cf95edb67f7b)


<p>
Continue Setting up osticket in the browser > MySQL Database: osTicket (create this in Heidi SQL)
 > MySQL Username: root > MySQL Password: Password1 > Click “Install Now!”
</p>


![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/3ef27f1c-162f-4a17-9d0d-6fdfc12b8f05)
![image](https://github.com/nealzubin/osticket-prereqs/assets/145185495/386ab107-1458-4bed-a032-173b346f5bad)


<p>
Congratulations, hopefully it is installed with no errors! 
 Browse to your help desk login page: http://localhost/osTicket/scp/login.php
</p>



<h2>Clean Up</h2>

<p>
Delete: C:\inetpub\wwwroot\osTicket\setup
 Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>

<p>
Notes:
 - Browse to your help desk login page: http://localhost/osTicket/scp/login.php  
 - End Users osTicket URL: http://localhost/osTicket/ 
</p>








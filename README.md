<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

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





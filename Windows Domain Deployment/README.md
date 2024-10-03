<img src="https://github.com/user-attachments/assets/d150deee-c0c2-4a12-b432-bf85c489721b" alt="Description of image" />

#

# Table of contents.

- [Table of contents.](#table-of-contents)
- [Project Overview.](#project-overview)
- [Tasks](#tasks)
- [Tools and Utilities.](#tools-and-utilities)
- [Skills Gained.](#skills-gained)    
- [Network Diagram](#network-diagram)
- [Links.](#links)
- [Project Walkthrough](#project-walkthrough)
    - [Virtual Machine Setup](#virtual-machine-setup)
    - [Windows Server 2022 Installation](#windows-server-2022-installation)
    - [Domain Deployment - Active Directory](#domain-deployment---active-directory)


# Project Overview.
-The project walks through the deployment of Windows Server 2022 and promotes the server into a domain controller to host Active Directory Domain Services.

# Tasks
- First, we set up the Windows Server 2022 virtual machine.
- We then boot the virtual machine and install our server.
- After installing the server, we add the Active Directory role and features and promote the server into a Domain Controller.

# Tools and Utilities.
- Oracle VirtualBox.
- Windows Server 2022.
- Active Directory.
- Server Manager.

# Skills Gained.
- Virtualization.
- Windows Server Installation.
- Active Directory Roles and Features.
- Server Management.

# Network Diagram.



# Links.
- Windows Server 2022
- VirtualBox
- Windows 10 Enterprise

# Project Walkthrough

## Virtual Machine Setup
-The virtual machine for the server is created using VirtualBox 
- VirtualBox is an open-source hypervisor created and maintained by Oracle.
 
-To create a new virtual machine we need to open VirtualBox click New

![VM 1](https://github.com/user-attachments/assets/b6f91d4c-37cf-47c1-ae4b-af1ae1a90e16)

-After clicking new, we need to name our virtual machine, choose where to store it, and choose an operation system type and version which is Windows Server 2022 for our Domain Controller

![VM 2](https://github.com/user-attachments/assets/2a65cc06-eaae-4bd6-8090-1bf88bc7f007)

-For the VM hardware we need to allocate memory and CPU cores. The minimum is 2 gigabytes for Server GUI. We would allocate higher RAM and CPU cores to accommodate our enterprise environment. 

-The Server would also be on a dedicated Server, a type 1 hypervisor or the cloud server.

![VM 3](https://github.com/user-attachments/assets/dc5a7bd1-9cac-4c8c-9284-0b955a822fb4)

-In this step, we create a Virtual Hard Disk(VHD) to store our server and other applications. In this case, I made a new VHD and allowed the VM to use it as needed without pre-allocating the full storage 

![VM 4](https://github.com/user-attachments/assets/77dfd428-695a-4455-99dc-c8e2158e4a36)

-The summary shows the basic setup.

-The server ISO image will be attached during the configuration.

![VM 5](https://github.com/user-attachments/assets/7e76767f-94ce-4ca4-8d21-97d78349ec63)

-To complete the VM setup we modify the settings to be ready for booting and installing the server.

![VM 6](https://github.com/user-attachments/assets/3afe9bbf-2ac0-4d21-8afb-247ec1a7e492)

-We name or confirm the name and operating system type and version.  

![VM 7](https://github.com/user-attachments/assets/9bfdc0be-1730-4d4c-b709-2c6bec8ceaa4)

-To make copying easy we allow bidirectional clipboard sharing

-This allows us to copy files and executables from our host machine to the server or vice versa.

![VM 8](https://github.com/user-attachments/assets/d8bc54df-a1b5-4ab5-81b3-f1b27ab95cdd)

-We now confirm the memory (RAM) and the CPU Cores we assigned.

-It's also time to modify the boot order, putting first the optical drive to which we're attaching the ISO Image for installing the server.

-The second boot device is the Virtual Hard Disk. It will store the operating system after installation and it will become our boot device after installation. 

![VM 9](https://github.com/user-attachments/assets/0e85c9c5-009a-4d69-9d4b-422bf662234d)

![VM 10](https://github.com/user-attachments/assets/155b7307-a648-4dec-ae8c-62be931d70e6)

-It's time to attach our ISO image to the optical drive to boot from it and install our server into the Virtual Hard Disk (VDI).

-After installing the server using the ISO Image, we will detach it and boot from the OS in our VDI.

![VM 12](https://github.com/user-attachments/assets/0765f97a-adbc-46d6-87db-912dcbcec0b9)

![VM 13](https://github.com/user-attachments/assets/ee43e9e1-14c4-450f-865b-b51909da1b55)

![VM 14](https://github.com/user-attachments/assets/c96bdae3-c5c5-41df-9633-2985cf058235)

-Now we set up Networking for our virtual machine network settings
- I've set the Adapter to be on a NAT network. The VM will be isolated but still access the internet using the NAT engine from the hypervisor.

![VM 15](https://github.com/user-attachments/assets/4fd768bd-31d5-40f0-b3db-d76989abd2d3)

-A shared folder has been added to share files and executables between the host and the server.

![VM 16](https://github.com/user-attachments/assets/a5efdee4-1ed9-4fba-b8c8-1fd7ececd0f1)

![VM 17](https://github.com/user-attachments/assets/01916e78-cfb6-4a67-93ea-a63da85a6532)

-Summary.
- The Virtual Machine has been set up and we are ready to install our server

![VM 18](https://github.com/user-attachments/assets/6dea16ea-2d7e-4a8e-8871-9f1b8be29619)

## Windows Server 2022 Installation

-It's time to start our VM to start the installation. 
- To do that we press start to boot our VM 

![VM 1](https://github.com/user-attachments/assets/72c762d8-2371-4976-9d40-236e3d03c47b)

-We continue the installation by choosing language and date preference

![VM 1](https://github.com/user-attachments/assets/37028935-2dc4-4c17-bb62-756d3e339b5b)

-From here we start with our fresh installation.

![VM 2](https://github.com/user-attachments/assets/c8522a60-22a0-4ba1-ab9d-f792d570140f)

-We want to choose the standard edition as we're not running our server in a highly virtualized environment. 

-There are 4 versions released with Windows Server 2022
- Windows Server 2022 Essential: Ideal for Small Businesses with 25 users and 50 devices.
- Windows Server 2022 Standard: Ideal for Physical or minimally virtualized environments.
- Windows Server 2022 Datacenter: Ideal for highly virtualized datacenters.
- Windows Server 2022 Azure: Ideal for running server as a VM in Azure 

![VM 3](https://github.com/user-attachments/assets/b4e24a69-5078-43af-957b-fe0747a35bde)

![VM 4](https://github.com/user-attachments/assets/a79a806c-3e48-406c-8b19-c4c531862bb1)

-We choose custom installation to achieve a fresh install

![VM 5](https://github.com/user-attachments/assets/3891fe1a-8791-41b5-948c-86a0f3c13f55)

-We want to store the operating system in the Virtual Hard Disk(VDI) we created.

-We can then start our installation.

![VM 6](https://github.com/user-attachments/assets/ddb9c2d4-6970-481f-a4a7-8fbed6956964)

![VM 7](https://github.com/user-attachments/assets/eb754c27-15b7-43ba-a5a7-b2cac84f0457)

-A strong password for the built-in administrator account needs to be created at this point to use for logging in.

![VM 8](https://github.com/user-attachments/assets/af7f25ad-008b-4447-962c-b722f5e1748d)

-Installation has been done. We can log in to the server.

![VM 10](https://github.com/user-attachments/assets/894fc7a3-b267-4356-93bb-e60786eeb0c9)

![VM 11](https://github.com/user-attachments/assets/c019bcb4-7f5a-4508-87b8-fdc41c5a3c43)

-We're done installing the Server. There are post-installation tasks to do before we can add any roles and features to our server
- Updating the server.
- Disabling IPv6.
- Renaming the Server.
- Verifying Activation

-Renaming the Server to identify it on the network.
![VM 17](https://github.com/user-attachments/assets/4a887643-5317-434c-9eb0-b8a6e4191d06)

-Installing the latest updates.

![VM 22](https://github.com/user-attachments/assets/12467ef1-2cdf-447a-bff5-4e15f769b3f5)

-Disable IPv6 to avoid network issues.

![VM 20](https://github.com/user-attachments/assets/25e89cc2-f99e-44ea-b337-070bfa7bb747)

-Lastly, we need to verify the activation and restart the server

![VM 18](https://github.com/user-attachments/assets/04d5c10d-da85-4b7d-aa35-decceb33ed7b)

-Now everything looks good we can move on to install the Active Directory Domain Services

![VM 23](https://github.com/user-attachments/assets/29156a4e-95c7-4b7d-8fbd-578142fc9bd7)

## Domain Deployment - Active Directory












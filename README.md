# ActiveDirectoryLab
A basic Lab for building and working with Active Directory

## In This Lab I...
 - I created Virtual Machines using Virtual Box for a Windows Server 2019 system and a client.
 - Set up the Server as a domain controller with a Domain, NAT and DHCP scope, along with using a script to create 1000+ users

## Languages and Utilites Used
- Oracle Virtual Box
- Powershell

## Languages and Utilites Used
- Windows 10
- Server 2019

### The Diagram setup for this Lab
![alt text](https://github.com/WoodsC94/ActiveDirectoryLab/blob/main/Screenshot%202024-04-23%20111123.png)

### Lab Walkthrough
![alt text](https://github.com/WoodsC94/ActiveDirectoryLab/blob/main/Screenshot%202024-04-23%20113220.png)
- After Installing and getting Server 2019 set up in Virtualbox I first set up the Directory Domain Services.
- created a domain as a forest called mydomain.com
  
![alt text](https://github.com/WoodsC94/ActiveDirectoryLab/blob/main/Screenshot%202024-04-23%20123312.png)
- From there I created an organizational unit for all Admins on this domain. 

![alt text](https://github.com/WoodsC94/ActiveDirectoryLab/blob/main/Screenshot%202024-04-23%20123335.png)
- Then, I created a dedicated domain admin account, for extra security.
- From here on all changes were made under the newly created admin account.

![alt text](https://github.com/WoodsC94/ActiveDirectoryLab/blob/main/Screenshot%202024-04-23%20123835.png)
- I installed the role of routing and remote access
- Configured the Server to use NAT to make the internal clients be able to access the internet through the domain controller.

![alt text](https://github.com/WoodsC94/ActiveDirectoryLab/blob/main/Screenshot%202024-04-23%20125021.png)
- Then I set up the role for a DHCP server and make a scope of IP address range for the network.
- Set the Lease for IP address reservation for 8 days, production enviroments may need longer or shorter depending on needs.
-  Scope range is 172.16.0.100 - 172.16.0.200
-  Set the the domain controller as the Default Gateway, and DNS server.
-  After setup I autorized the domain controller to accept the changes.

![alt text](https://github.com/WoodsC94/ActiveDirectoryLab/blob/main/Screenshot%202024-04-23%20131119.png)
- Saved the script to the desktop
- Opened Powershell ISE as an administrator
- I Set-ExecutionPolicy as Unrestricted so I would be able to execute the script.
- I changed directory into my desktop folder to run the script.
- The script uses a .txt file of names to generate users, using first initial and last name, as well as set up a second organizational unit for the users to be in.
- [Script that I used to bulk create Users](https://github.com/joshmadakor1/AD_PS)

![alt text](https://github.com/WoodsC94/ActiveDirectoryLab/blob/main/windows10%20client1_2024-04-23%20131826.png)
- After the script finished, I then set up a Windows 10 Pro VM to act as a client.
- Then I pinged gooogle.com and checked ipconfing in the command line to ensure the client had connectivity to the internet throught the domain controller.
- Renamed the client PC to CLIENT1 and also joined the domain in the same setup. I sucessfully joined the domain through a created user login.

![alt text](https://github.com/WoodsC94/ActiveDirectoryLab/blob/main/CLIENT1_connected.png)
![alt text](https://github.com/WoodsC94/ActiveDirectoryLab/blob/main/CLIENT1_connectedv2.png)

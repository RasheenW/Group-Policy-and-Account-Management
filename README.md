<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1> Group Policy & Account Management </h1>
This tutorial outlines how use use Group Policy and Manage User accounts within Activer Directory <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Windows PowerShell ISE

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

 <h2>Objectives </h2>

- Create Users
- Manage User Accounts
- Create Group Policies

<h2> Creating Users </h2>

Log into DC-1 as your admin user, We will now use a script within Windows Powershell ISE to create a bunch of users for us to get more aclimated with Active Directory administration. Open Windows Powershell ISE as an Administrator, Click the link below and copy the raw script from the Github Repository by clicking these 2 boxes

<img src=https://i.imgur.com/qRL8xNs.png>

- [Script](https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1) 

<img src=https://i.imgur.com/tThoqFI.png>

In Windows Powershell ISE open a new script, Save it under any name then paste the script we copied earlier into the file itself

<img src= https://i.imgur.com/uy48Sso.png>

This script will generate up to 10000 users which isn't necessary so feel free to let it run up to roughly 1000. Note the password for every user account will just be "Password1". As long as you have the "_EMPLOYEES" OU the script should run normally, Now click the Green Arrow and let the script run for a period of time

<img src=https://i.imgur.com/tBADt7i.png>

Once you have a handfull of Users created, Pick a random one and relog into Client-1 with the created User

<img src=https://i.imgur.com/VA39t3t.png>

If you was able to log in as your User, We can proceed onto Managing these Accounts

<h2> Account Management </h2>

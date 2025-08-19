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
- [Script](https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1)
  
<img src=https://i.imgur.com/qRL8xNs.png>

<img src=https://i.imgur.com/tThoqFI.png>

In Windows Powershell ISE open a new script, Save it under any name then paste the script we copied earlier into the file itself

<img src= https://i.imgur.com/uy48Sso.png>

This script will generate up to 10000 users which isn't necessary so feel free to let it run up to roughly 1000. Note the password for every user account will just be "Password1". As long as you have the "_EMPLOYEES" OU the script should run normally, Now click the Green Arrow and let the script run for a period of time

<img src=https://i.imgur.com/tBADt7i.png>

Once you have a handfull of Users created, Pick a random one and relog into Client-1 with the created User

<img src=https://i.imgur.com/VA39t3t.png>

If you was able to log in as your User, We can proceed onto Managing these Accounts

<h2> Group Policy </h2>

Before we actually proceed, We need to update the Group Policy to have Account Lockouts because it is not on by default, Log into dc-1 and in the search bar type "Run". Within that enter "gpmc.msc", click Ok and the Group Policy Management Console should appear
After it does drop down the categories on the left until you see "Default Domain Policy" then right click it to edit as shown in the image below

<img src=https://i.imgur.com/LOu5ZWA.png>
<img src=https://i.imgur.com/xGTBsQV.png>

Now within the editor we just have to expand in this order, Computer Configuration > Policies > Windows Settings > Security Settings > Account > Polices > Account Lockout Policy

<img src=https://i.imgur.com/gTG4gHy.png>

The policies we will be adjusting is shown below in this manner by right clicking each one and selecting "Properties"
- Account lockout duration: 30 minutes
- Account lockout threshold: 5 invalid logon attempts
- Allow Administrator account lockout: Enabled
- Reset account lockout counter after: 10 minutes

<img src=https://i.imgur.com/IKM4of2.png>

To finish this step off we will be logging back into Client-1 with jane_admin to force update the policy so we don't have to wait for it to update on its own. Simply we will just open the Command Prompt and type gpupdate /force
<img src=https://i.imgur.com/81AFXjR.png>

<h2> Unlocking Accounts </h2>
Within dc-1, Pick a random user and log into client-1 as the user with the wrong password up to 5 times to create a log history and force it into account lock out. We will find this user through Active Directory Users and Computers
The account I chose was cema.mam, Once you have failed to log in up to 5 times with your selected account (To check if its locked, try using the Password1 and see if it lets you in).

<img src= https://i.imgur.com/9BKlC7U.png>

In dc-1 right click Employees_ in Active Directory Users and Computers and click "Find" to easily locate your user

<img src=https://i.imgur.com/XyPzGqy.png>

Once you do double click on their name, Proceed to click Account, Check the box that says "Unlock Account" and click apply. Proceed to log into your users account again 

<img src=https://i.imgur.com/HzYfd2Z.png>

<h2> Password Resets </h2>

This part is relatively simple, You would find the account the same way as above but instead you right click on the name and click "Reset Password". What's nice about this is that you can also unlock accounts as well at the same time.

<img src=https://i.imgur.com/XtdSKh1.png>
<img src=https://i.imgur.com/7jX1Em3.png>

<h2> Enabling and Disabling Accounts </h2>

You can also do this from the Find menu, Right click on the user and click "Disable Account". If you click "Find now" immediately after this you'll see their user icon updates to showcase its a disable account

<img src= https://i.imgur.com/0Bcvqrl.png>

Now if you attempt to log into that user account this prompt will show 

<img src=https://i.imgur.com/toCVJ8z.png>

We can easily enable the account again from the same menu

<h2> End </h2>

Congrats on understanding how to use Active Directorym, This will be the end of this demostration

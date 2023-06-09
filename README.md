# Create-Network-File-Shares
In this lab I will demonstrate how to create file shares, grant and restrict access to the shares, and create and add a member to an Active directory security group.

<p align="center">
<img src="https://i.imgur.com/LI6HnVC.png" alt="Traffic Examination"/> 

<img src="https://i.imgur.com/zd4QKPu.png" alt="Traffic Examination"/>
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Users And Computers

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Windows Server 2022

<h2>High-Level Steps</h2>

- Logon to the domain controller, create four folders on C:\
  Read-access, Write-access, No-access and Accounting
- Share and set access permissions for each folder
- Logon to the client computer and attempt to access each of the new folders
- Create a Security Group named “Accountants” on the domain controller
- Logon to the workstation with one of the new domain users, try to access the Accounting folder.
- Add the new domain user to the “Accountants” security group.
  Try to access the folder again.


<h2>Actions and Observations</h2>

<b>Part 1</b> <h4>Create Four Folders On Drive C:<h4>

<p>Log into DC01 
<p>
<img src="https://i.imgur.com/x1UPASQ.png" height="40%" width="401" alt="Disk Sanitization Steps"/>

<p>On DC01 create four folders:

Click Explorer > this computer > c:\ 
	Right-click > new > folder
<p>
<img src="https://i.imgur.com/UuQNQuq.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

<p>Rename the four folders as follows:
<p>
<img src="https://i.imgur.com/4IRfQeJ.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

<b>Set the following access permissions for each folder</b>

<img src="https://i.imgur.com/CNj4BxF.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>


<h4>Part 2</h4>
<h4>Share and set access permissions for each folder</h4>

<p>Right-click the  “Read-access” folder > properties
<p>
<img src="https://i.imgur.com/Xv4B0dI.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

<p>Select the sharing tab > share
<p>
<img src="https://i.imgur.com/2XG5C8W.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

<b>Select people or groups to share the folder</b>

<p>Share this folder with “Domain Users”  > add
<p>
<img src="https://i.imgur.com/IeexWWx.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>Select “share”
<p>

<p>The folder is shared > select “done”
<p>
<img src="https://i.imgur.com/lb9DZjX.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>Here is the path to the folder > close
<p>
<img src="https://i.imgur.com/HtKuUdk.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

<p>Repeat this procedure for “Write-access”,
leave the Accounting folder as is for now.
</p>
<img src="https://i.imgur.com/wGt0d2L.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

<p>Right-click the “No-access” folder > properties > share tab > share

Type “Domain Admins” or you can search for “Domain Admins”
	
using the following procedure:
</p>

<p>=====================================================================================


<p>In the search box type “domain” > when the pop-up displays select “find”
<p>
<img src="https://i.imgur.com/efZikqh.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>Type “domain” in the object field > check names
<p>
<img src="https://i.imgur.com/xGfDfUV.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/6vkt0Tg.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<i>You can use this method if you have trouble finding a user or group</i>

<p>=====================================================================================


<b>Change the permission for the “No-access” folder to “Read-write” > share</b>

<img src="https://i.imgur.com/8Hp2mkn.png" height="40%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/2WjrM26.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<b>Set access permissions for the “Write-access” folder</b>

<p>The “Read-access” folders permission was set to “Read” by default
	
Right-click  the “Write-access” folder > properties > sharing tab >
	
change permissions to “Read-write”
</p>

<p>Select “share” 
This folder has “write access” permissions
<p>
<img src="https://i.imgur.com/G0KKRLu.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<h4>Part 3</h4>

<h4>Logon to the client computer and attempt to access each of the new folders</h4>

<p>Using the public IP address, Log into GTWS-01 with one of the new users we created
<p>
<img src="https://i.imgur.com/KL03C5z.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

<p>Goto the file explorer<p>
<p>Try to access the three folders that were created.<p> 
<p>Which folders can we access?<p>
<p>Which folder can we access and modify?
<p>

<p>Try to access the “read-access” folder using the following path
“\\DC01\read-access”
<p>
<img src="https://i.imgur.com/Uhnf1rI.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>Here are the shares that are stored on DC01
<p>
<img src="https://i.imgur.com/nHhGGlw.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>Can we access the “read-access” folder?  Yes
	
Can we modify files inside  the “read-access” folder? No.
	
**the permission is set to read-only
</p>
<img src="https://i.imgur.com/Epi6e3f.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/7c87NI5.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>Can we access the “write-access” folder? Yes.
	
Can we modify the “read-access” folder? Yes.
	
**the permission is set to read-write
</p>
<img src="https://i.imgur.com/p4ntJ2D.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>I am able to create and modify files inside the “write-access” folder
<p>
<img src="https://i.imgur.com/h5Mk2F1.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>Can we access the “no-access” folder? No.
	
*** The permission is set to “read-write”; however,
	
this user cannot access the folder because the user is not a member
	
of the "Domain Admins” group.
</p>
<img src="https://i.imgur.com/mFUDNcP.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>On GTWS-01

Log out and log in with a “Domain Admin” account
<p>
<img src="https://i.imgur.com/cHpDKUV.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

<p>Try to access and modify the “no-access” folder
<p>
<img src="https://i.imgur.com/vQpnKhO.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>Can I access the “no-access” folder?  Yes
	
Can I write to the “no-access” folder? Yes
	
I can read and write to this folder because the access is set for “Domain Admins”
</p>
<img src="https://i.imgur.com/JEtEDYC.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<h4>Part 4</h4>

<h4>Create a Security Group named “Accountants” on the domain controller</h4>

<p>Log on to DC01 > Server Manager >
	
Active Directory Users and Computers >
	
right-click the domain > New > Group
</p>
<img src="https://i.imgur.com/rjiQN97.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

<p>Name the Group > Accountants
<p>
<img src="https://i.imgur.com/aujd53e.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>Here is the new group
<p>
<img src="https://i.imgur.com/1rK2pI6.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

<p>In the file explorer, go to the accounting folder,
	
set the permissions on the Accounting folder to:

Group :       Accountants
	
Permissions:  Read-Write
</p>
<img src="https://i.imgur.com/LLTJz4p.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/3VrUOFz.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

<h4>Part 5</h4>

<h4>Add the new domain user to the “Accountants” security group</h4>

<p>Go to GTWS-01
	
Log on as one of the new users
</p>
<img src="https://i.imgur.com/xaWJkjl.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

<p>Go to the Accounting folder
	
Can the user access the folder?
	
No, this user is not a member of the “Accountants security group”
</p>
<img src="<img src="https://i.imgur.com/BV7KjCV.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

	
<p>Log out of GTWS01
<p>

<p>Add domain user “cuv.rem” to the Accountants group

On DC01 > server manager > active directory users and computers > 
													   
Select view > advanced features >
</p>
<img src="https://i.imgur.com/sXNE1Jv.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>Right-click Accountants group > properties
<p>
<img src="https://i.imgur.com/a7y9vwI.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>

<p>Select the Members tab > add > cuv.rem> check names > ok
<p>
<img src="https://i.imgur.com/mLoWbSK.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

<p>Apply > ok
<p>
<img src="https://i.imgur.com/7vFENG9.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

<p>Goto GTWS-01

Log out and log back in with user “cuv.rem”
<p>
<img src="https://i.imgur.com/wdamvpc.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>

<i>Can this user access the Accounting folder?
Yes, because the user is now a member of the Accountants security group</i>




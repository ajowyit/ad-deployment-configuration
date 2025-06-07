<p align="center">
<img width="450" height="250" alt="Microsoft Active Directory Logo" src="https://github.com/user-attachments/assets/cd75c7f5-fba1-4682-a616-dc487e761fbc"
 alt="Microsoft Active Directory Logo"/>
</p>

<h1>Deployment and Configuration of Active Directory in the Cloud</h1>

In this tutorial, we walk through deploying Active Directory in a simulated on-premises environment using Azure Virtual Machines.
<br />

<h2>⚠️ Prerequisites</h2>

- [Creating Virtual Machines in the Cloud](https://github.com/ajowyit/creating-virtual-machines)
  
- [Create Active Directory Infrastructure in Azure](https://github.com/ajowyit/create-ad-infrastructure)

<h2>💻 Environments and Technologies Used</h2>

- Microsoft Azure 
- Windows App (for macOS)
- Remote Desktop
- Active Directory Domain Services

<h2>👨‍💻 Operating Systems Used </h2>

- macOS Sequoia
- Windows Server 2022
- Windows 10 (21H2)

<h2>📋 High-Level Steps</h2>

- Step 1: Install Active Directory
- Step 2: Create a Domain Admin User within the Domain
- Step 3: Join Client-1 to the Domain
- Step 4: Setup Remote Desktop for non-admin users on Client-1

<h2>⚙️ Deployment and Configuration Steps</h2>

<h3>Step 1: Install Active Directory</h3>
<p>
<img width="1699" alt="Screenshot 2025-06-05 at 2 32 44 PM" src="https://github.com/user-attachments/assets/cb2bc07f-b070-4f37-b13c-53ed085cf0a9" />

<img width="786" alt="Screenshot 2025-06-05 at 2 32 59 PM" src="https://github.com/user-attachments/assets/c060829e-c3ed-418d-bd95-ac8ab90617f6" />

<img width="785" alt="Screenshot 2025-06-05 at 2 33 37 PM" src="https://github.com/user-attachments/assets/fd0e9864-d4d0-419b-a128-8e3dae11a458" />

<img width="785" alt="Screenshot 2025-06-05 at 2 33 49 PM" src="https://github.com/user-attachments/assets/48b9f342-eaa5-474d-963b-3c69b1c5c4d7" />

<img width="787" alt="Screenshot 2025-06-05 at 2 34 16 PM" src="https://github.com/user-attachments/assets/0438558b-f2ca-4cf1-990b-31af50d7bf8d" />

<img width="788" alt="Screenshot 2025-06-05 at 2 34 28 PM" src="https://github.com/user-attachments/assets/8ecd3d73-1812-435f-979f-9fdd531ae9da" />

<img width="787" alt="Screenshot 2025-06-05 at 2 34 41 PM" src="https://github.com/user-attachments/assets/353ef1af-7094-4d5d-9f4a-3fe1e1d03716" />

<img width="787" alt="Screenshot 2025-06-05 at 2 35 47 PM" src="https://github.com/user-attachments/assets/4d6b63b0-1ef5-4f44-bd99-2acf4018b357" />

<img width="785" alt="Screenshot 2025-06-05 at 2 35 38 PM" src="https://github.com/user-attachments/assets/2fd5c34f-6197-4ab4-9ed9-d003d32950f7" />

<img width="787" alt="Screenshot 2025-06-05 at 3 14 36 PM" src="https://github.com/user-attachments/assets/6c4aeaf6-b0dc-4a34-9897-5a3015dc954a" />

</p>

<p>
- Login into DC-1 using RDP/Remote Desktop/Windows App.
</p>
<p>
- In Server Manager, select "Add roles and features". This will open the "Add Roles and Features Wizard" window. You will start at "Before You Begin". Click on "Next >".
</p>
<p>
 - In "Installation Type"/"Select installation type", make sure "Role-based or feature-based installation" is selected. Click on "Next >".
</p>
<p>
 - In "Server Selection"/"Select destination server", make sure that DC-1 is the only one listed and selected. Click on "Next >".
</p>
<p>
 - In "Server Roles"/"Select server roles", select "Active Directory Domain Services". The "Add Roles and Features Wizard" window will pop up asking you if you want to add features required for Active Directory Domain Services. Click "Add Features". "Active Directory Domain Services" should now be selected. Click on "Next >".
</p>
<p>
 - Click "Next >" until you get to "Confirmation"/"Confirm installation selctions". Click "Install" then click "Yes" when asked about allowing automatic restarts if a restart is required in the popup window. Once the feature installation finishes, click "Close".
</p>
<br />

<p>
<img width="1710" alt="Screenshot 2025-06-05 at 4 38 02 PM" src="https://github.com/user-attachments/assets/0cd56d47-de0b-471e-a065-7fb5d98a009a" />
</p>

<p>
- Find the flag and yellow tringle at the top right of the screen in Server Manager and click it.
</p>
<p>
 - Clock on "Promote this server to a domain controller".
</p>
<br />

<table>
  <tr>
    <td>
      <img width="761" alt="Screenshot 2025-06-05 at 4 38 19 PM" src="https://github.com/user-attachments/assets/bfd0382e-1118-4ba1-b684-e3006986c515" />
    </td>
    <td>
      <img width="761" alt="Screenshot 2025-06-05 at 4 38 52 PM" src="https://github.com/user-attachments/assets/054d8389-4ee6-4ed6-8bfb-81b77f4be046" />
    </td>
  </tr>
</table>
<p>
 - This hshould open up the Active Directory Domain Services Configuration Wizard in a popup window. In "Deployment Configuration", under "Select the deployment operation", select "Add a new forest". Name it "mydomain.com" and then click on "Next >".
<p> 
 - In "Domain Controller Options", for the DSRM password, just use Password1. We won't be using this at all so it is unimportant. Click on "Next >" until you get to Prerequisites Check. In "DNS Options" if "Specify DNS delecgation options" is checked, uncheck it.</p>
<br />

<p>
 <img width="763" alt="Screenshot 2025-06-05 at 4 42 32 PM" src="https://github.com/user-attachments/assets/ef98658f-cf0d-4cd8-96c3-7812a0aaca86" />
</p>

<p>
 - After clicking "Next >" until all options have been configured, click "Install" to start the installation.
</p>
<p>
 - Once the install is finished, DC-1 will reboot. Then Remote Desktop back into DC-1 as a domain user
</p>
<br />

<p>
<img width="1013" alt="Screenshot 2025-06-05 at 5 26 27 PM" src="https://github.com/user-attachments/assets/6e9d5081-e79f-4d9a-9b75-e9005a3cd94e" />
</p>
<p>
 - Remote Desktop back into DC-1. Since DC-1 is now a domain controller and on the domain, you have to specify which domain, and that you want to log on as a domain user.</p>  
<p>- When logging into DC-1 as a domain user, enter "mydomain.com\ajowyit" (mydomain.com\username) and your password</p>
<p>- This will log us in as a specific user within the domain.</p>
<br />

<h3>Step 2: Create a Domain Admin User within the Domain</h3>

<p>
 <img width="836" alt="Screenshot 2025-06-06 at 6 40 23 PM" src="https://github.com/user-attachments/assets/ab307b12-26f0-4391-b01e-e2b395bb7543" />
</p>

<p>
 - Once logged back into the DC-1 virtual machine, open up Windows Administrative Tools.
</p>

<p>
 <img width="1125" alt="Screenshot 2025-06-06 at 6 41 39 PM" src="https://github.com/user-attachments/assets/3b683213-4e74-4615-bbe9-2c6f643c34a3" />

 <img width="1399" alt="Screenshot 2025-06-06 at 6 42 39 PM" src="https://github.com/user-attachments/assets/51b476b8-3064-47d3-9a4e-ba1a028336f3" />
</p>

<p>
 - Once the Administrative Tools window is open, click on "Active Directory Users and Computers". This will open the "Active Directory Users and Computers" window. 
</p>


<p>
 <img width="754" alt="Screenshot 2025-06-06 at 6 42 50 PM" src="https://github.com/user-attachments/assets/9d165767-f5aa-4459-8797-9cde490d938d" />

 <img width="438" alt="Screenshot 2025-06-06 at 6 43 03 PM" src="https://github.com/user-attachments/assets/385f3900-27f1-4ffc-ae10-e49ebee5a1bd" />
</p>

<p> 
 - Now we will create a new Organizational Unit (OU). 
</p>
<p>
 - Right-click mydomain.com -> New -> Organizational Unit. This will open a window to create a new Organizational Unit.
</p>
<p>
 - Name the new Organizational Unit "_EMPLOYEES". Make sure there is an underscore in the beginning. Finish by clicking "OK". 
</p>

<br />

<p>
 <img width="438" alt="Screenshot 2025-06-06 at 6 44 31 PM" src="https://github.com/user-attachments/assets/728e9299-0981-4ca4-a2db-29663b224530" />
</p>

<p>
 - Next we will create another new Organizational Unit for admins called _ADMINS.
</p>
<p>
 - Right-click mydomain.com -> New -> Organizational Unit to create the new one. Name this OU as _ADMINS (don't forget the underscore). Click OK.
</p>

<br />

<p>
<img width="755" alt="Screenshot 2025-06-06 at 6 45 00 PM" src="https://github.com/user-attachments/assets/536766f9-41a5-4ee9-bf89-1b7b117bf4a8" />
 
<img width="757" alt="Screenshot 2025-06-06 at 6 45 15 PM" src="https://github.com/user-attachments/assets/1ca6be69-ed34-4df4-96fe-8cd01b02ab14" />
</p>
<p>
 - Now, make sure mydomain.com is selected and select the Refresh icon at the top. This will move our new OUs to the top of the list for easier location and access.</p>  
<br />

<p>
<img width="752" alt="Screenshot 2025-06-06 at 6 47 25 PM" src="https://github.com/user-attachments/assets/439df63f-4d73-498a-be6a-ec45e5e31c32" />
<img width="436" alt="Screenshot 2025-06-06 at 6 47 51 PM" src="https://github.com/user-attachments/assets/d45be76a-d273-49a5-811b-c69aa434a3ff" />
<img width="437" alt="Screenshot 2025-06-06 at 7 00 51 PM" src="https://github.com/user-attachments/assets/ae2fd2c0-6380-4673-8818-a79af2e5ee43" />
<img width="436" alt="Screenshot 2025-06-06 at 7 01 50 PM" src="https://github.com/user-attachments/assets/527c1562-005b-46d0-b32b-4af347242b5e" />
</p>
<p>
 - Next, we will create a new user.
</p> 
<p>
 - Right-click _ADMINS -> go to "New" -> click "User".
</p>
<p>
 - Name the new user as Jane Doe, with the first name "Jane" and the last name "Doe". Click "Next >".
</p>
<p>
 - Use the same password as you did for DC-1 to make it easy to remember. Select "Password never expires". In the real world we shouldn't do this for security purposes but for the sake of this project it is okay. Click "Next >".
</p>
<p>
 - Finally, click "Finish" to create the new user. 
</p>
<br />


<p>
<img width="754" alt="Screenshot 2025-06-06 at 7 04 07 PM" src="https://github.com/user-attachments/assets/4bfb24c0-e474-48c9-a5b1-76e3edbc7bb5" />
<img width="697" alt="Screenshot 2025-06-06 at 7 08 37 PM" src="https://github.com/user-attachments/assets/9862cf7b-6a4c-475b-bcbd-825676c6e72a" />

<img width="713" alt="Screenshot 2025-06-06 at 7 08 44 PM" src="https://github.com/user-attachments/assets/a48f984f-0450-48a4-8da9-1a0e944b685f" />


</p>
<p>
 - Now, we will make "Jane Doe" account we just created a Domain Admin by adding it to the built-in "Domain Admins" Security Group. 
</p> 
<p>
 - Open the _ADMINS folder by clicking on it -> right-click Jane Doe -> click "Properties". This will open the Jane Doe Properties window.
</p>
<p>
 - Click on "Member Of" at the top. Then click "Add...", the Select Groups window should pop up. Under "Enter the object names to select (examples):" type in "domain admins". Click "Check Names". 
</p>
<p>
 - Domain names should now be capitalized and underlined. Click "OK"
</p>
<br />

<p>
<img width="410" alt="Screenshot 2025-06-06 at 7 10 01 PM" src="https://github.com/user-attachments/assets/aa5bf164-6e64-4691-9c00-72db9cf2e618" />
</p>

<p>
 - Jane Doe is now a Domain Admin. Click "OK".
</p>
<p>
 - Next, log out and close the DC-1 connection. Log back into DC-1 with Jane Doe's Admin login. We will use this account from now on. Make sure you take a note of Jane Doe's login info for later use.
</p>
<br />

<h3>Step 3: Join Client-1 to the Domain</h3>

<p>
<img width="784" alt="Screenshot 2025-06-06 at 11 36 47 PM" src="https://github.com/user-attachments/assets/28d530e4-e647-4db5-8ae5-60395b434935" />
<img width="1201" alt="Screenshot 2025-06-06 at 11 36 55 PM" src="https://github.com/user-attachments/assets/accf5c9e-55cd-430e-8826-146d74bdf7d3" />
<img width="1202" alt="Screenshot 2025-06-06 at 10 35 17 PM" src="https://github.com/user-attachments/assets/972dd735-4ed5-422e-8403-ed232736ccba" />
<img width="324" alt="Screenshot 2025-06-06 at 10 36 04 PM" src="https://github.com/user-attachments/assets/abd026e8-0d6d-42ca-9b87-6fac66dafed7" />
</p>
<p>
 - Log into Client-1 as the original local admin. (ajowyit) </p>
<p>
 - Open System from the start menu.
</p>
<p>
 - Click on "Rename this PC (advanced)". If you don't see this option at first, maximze the window or expand it. The System Proerties window will pop up.</p>
<p>
 - Click "Change..."
</p>
<p>
 - Under "Member of" select "Domain". Type in mydomain.com. Click "OK".
</p>

<br />


<p>
<img width="1203" alt="Screenshot 2025-06-06 at 10 37 41 PM" src="https://github.com/user-attachments/assets/f36208b3-4163-4ca2-abaa-56cdb2bc415b" />
</p>
<p>
 - Join the domain. We will use the jane_admin account. </p>
<p>
 - Type in mydomain.com\jane_admin and the password. Click "OK". 
</p>
<br />

<p>
 <img width="963" alt="Screenshot 2025-06-06 at 10 38 46 PM" src="https://github.com/user-attachments/assets/56c3af0b-3dcd-4cfd-8939-423f08c79ef2" />
 <img width="950" alt="Screenshot 2025-06-06 at 10 38 57 PM" src="https://github.com/user-attachments/assets/4512910b-1b0f-436f-b45c-e4f042e518e9" />
</p>

<p>
 - Once you clicked OK, there should be a confirmation pop-up behind the System screen. Close that by clicking "OK".
</p>
<p>
 - Another message should pop up saying we need to restartClient-1 will need to restart out computer to apply these changes. Restart the computer.
</p>
<br />

<p>
 <img width="835" alt="Screenshot 2025-06-06 at 10 43 20 PM" src="https://github.com/user-attachments/assets/a5139ff1-1e05-4c27-9311-4f583069852b" />
<img width="754" alt="Screenshot 2025-06-06 at 10 51 33 PM" src="https://github.com/user-attachments/assets/d4e0b102-c8a2-40bd-b4c8-64bdd1dce365" />
<img width="754" alt="Screenshot 2025-06-06 at 10 53 06 PM" src="https://github.com/user-attachments/assets/cda463c7-fd71-4f7e-a56c-411f1f02e213" />

<img width="437" alt="Screenshot 2025-06-06 at 10 53 31 PM" src="https://github.com/user-attachments/assets/34fbfa62-2bc7-466f-a9d9-66423606e3fb" />

</p>

<p>
 - Log into DC-1 now. Use the jane_admin account. (mydomain.com\jane_admin) 
</p>
<p>
 - From the Start Menu, open Active Directory Users and Computers (ADUS). 
</p>
<p>
 - Expand mydomain.com and select Computers. We can verify Client-1 is here and has successfully joined the domain. 
</p>
<p>
 - Next, create a new Organizational Unit named _CLIENTS. Right-click "mydomain.com", go to "New", and click "Organizational Unit".
</p>
<p>
 - Name the new Organizational Unit, "_CLIENTS". Click "OK".
</p>

<br />

<p>
 <img width="755" alt="Screenshot 2025-06-06 at 10 53 53 PM" src="https://github.com/user-attachments/assets/bc96d607-dbf1-4155-9d6b-0826cd8dba12" />
<img width="756" alt="Screenshot 2025-06-06 at 10 54 06 PM" src="https://github.com/user-attachments/assets/0fb49e36-d7f1-4962-a4d6-8804fd2f49a5" />
<img width="753" alt="Screenshot 2025-06-06 at 10 54 32 PM" src="https://github.com/user-attachments/assets/62b8642f-eabc-448f-a868-fecd55aa031a" />
</p>

<p>
 - Go back to Computers. Drag Client-1 to the new _CLIENTS OU. 
</p>
<p>
 - Click "Yes" on the pop-up window. Refresh mydomain.com to move _CLIENTS to the top with the _ADMINS and _EMPLOYEES OUs (optional).
</p>
<br />

<h3>Step 4: Setup Remote Desktop for non-admin users on Client-1</h3>

<p>
<img width="500" height="400" alt="Screenshot 2025-04-23 at 11 21 16 AM" src="https://github.com/user-attachments/assets/147451a6-923c-4f87-b233-f63051053e16" />
</p>
<p>- Login into Client-1 with the jane_admin account.</p>
<br />

<table>
  <tr>
    <td>
      <img width="1000" alt="RD1" src="https://github.com/user-attachments/assets/4c7f51ab-4d66-42fd-a001-23bbf927603a" />
    </td>
    <td>
      <img width="1000" alt="RD2" src="https://github.com/user-attachments/assets/9b9e27b9-11d0-4721-8709-a6a4dffb6a28" />
    </td>
  </tr>
</table>
<p>- Right-click Start Menu -> select System -> click Remote Desktop. </p>
<p>- In Remote Desktop Users, click Add. </p>
<br />

<table>
  <tr>
    <td>
      <img width="1000" alt="RD3" src="https://github.com/user-attachments/assets/f6115248-d541-4fe0-8d65-9dacfaf79815" />
    </td>
    <td>
      <img width="1000" alt="RD4" src="https://github.com/user-attachments/assets/ac7c5331-de75-4065-8c37-8e8d62cd4ac0" />
    </td>
  </tr>
</table>
<p>- Type in domain users and click Check Names. Domain Users will capitalize and be underlined. Click OK. </p>
<p>- Confirm that MYDOMAIN\Domain Users is showing under Remote Desktop Users and click OK. </p>
<p>- Now, all users in the Domain Users group can Remote Desktop into Client-1. </p>
<br />

<h2>✅ Conclusion</h2>

<p>That wraps up our project — success! Active Directory has been successfully deployed, and next, we'll be adding a batch of users to the domain. Don’t forget to stop (turn off) your Azure VMs to avoid unnecessary charges. Thanks for following along, and we’ll see you in the next project! 😎     
</p>
<br />





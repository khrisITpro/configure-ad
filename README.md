<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Building a Simulated On-Premises Active Directory Infrastructure Using Azure Virtual Machines</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

 [![Watch the video](https://img.youtube.com/vi/AB0p-qio1Sc/0.jpg)](https://www.youtube.com/watch?v=AB0p-qio1Sc)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Install Active Directory Domain Services
- Step 2: Create a Domain Admin Account
- Step 3: Join Client-1 to the Domain
- Step 4: Manage Lab Costs
- Step 5: Enable Remote Desktop for Domain Users
- Step 6: Create Multiple Domain Users
- Step 7: Simulate and Configure Account Lockouts
- Step 8: Enable and Disable User Accounts
- Step 9: Review Security and Event Logs

<h2>Active Directory IT Support Lab</h2>

<p align="center">
  <img width="694" height="509" alt="ad config" src="https://github.com/user-attachments/assets/799ce933-665a-48a2-b26a-53402b2876f7" />

</p>
<p>
Step 1: Install Active Directory Domain Services: Log into DC-1 → Install Active Directory Domain Services → Promote it to a Domain Controller (DC) and create a new forest named "mydomain.com" → Restart the server and log back into it as mydomain.com\(Your_Username_Here).
</p>

<br />

<p>
  <img width="691" height="477" alt="ad config 2" src="https://github.com/user-attachments/assets/12909727-93ad-4028-9280-a35ba5e41b34" />

</p>
<p>
Step 2: Create a Domain Admin Account → In Active Directory Users and Computers (ADUC), create Organizational Units (OU) named "_EMPLOYEES" and "_ADMINS" → Add a new employee "Jane Doe" and add "kevin_admin" to the <b>Domain Admins</b> group → Log out of DC-1 and log back in as "mydomain.com\kevin_admin".
</p>

<br />

<p>
  <img width="691" height="483" alt="ad 3" src="https://github.com/user-attachments/assets/fc8e144e-4f82-4071-8723-6b4093395fd4" />

</p>
<p>
Step 3: Join Client-1 to the Domain → Restart Client-1 → Log in as the local admin and join it to mydomain.com → Verify in ADUC that Client-1 appears under the domain → Create a new OU named "_CLIENTS" and move Client-1 into it.
</p>

<br />


<p>
  <img width="1105" height="855" alt="ad4" src="https://github.com/user-attachments/assets/47bd2879-7d02-495a-86ee-7fad770698ad" />

</p>
<p>
Step 4: Enable Remote Desktop for Domain Users → Power on DC-1 and Client-1 → Log into Client-1 as <code>mydomain.com\kevin_admin</code> → Open System Properties and enable Remote Desktop access → Allow <b>Domain Users</b> access and confirm non-administrative users can now remotely connect.
</p>

<br />

<p>
  <img width="692" height="485" alt="ad5" src="https://github.com/user-attachments/assets/1baf15e2-4f01-4315-b87f-48aa167a3f0e" />

</p>
<p>
Step 5: Create multiple Domain Users → Log into DC-1 as an admin → Open <b>PowerShell ISE</b> as Administrator to run a script to bulk create multiple new users in the "_EMPLOYEES" OU → Verify the new accounts in ADUC → Attempt to log into Client-1 using one of the new user accounts.
</p>

<br />

<p>
  <img width="1479" height="893" alt="ad 6" src="https://github.com/user-attachments/assets/f40b7844-a28b-4bc0-b212-ac657c614b45" />

</p>
<p>
Step 6: Simulate and Configure Account Lockouts → On DC-1, pick a random user and attempt to log in 5 times using an incorrect password → Open Group Policy Management and configure the Account Lockout Threshold to 5 attempts → Retry logging in 5 times with a bad password → Observe that the account is now locked → Unlock the account in ADUC, reset the password, and confirm a successful login.
</p>

<br />

<p>
  <img width="1075" height="661" alt="ad 7" src="https://github.com/user-attachments/assets/88eee4ce-72db-47f3-a648-b71403f5f466" />

</p>
<p>
Step 7: Enable and Disable Accounts → On DC-1, disable a test user account in ADUC → Attempt to log in and observe the “account disabled” message → Re-enable the account and verify a successful login.
</p>

<br />

<p>
  <img width="1592" height="955" alt="ad 8" src="https://github.com/user-attachments/assets/f009565d-57da-462e-aa26-7dad21d1663f" />

</p>
<p>
Step 8: Review Security and Event Logs → Open Event Viewer on both DC-1 and Client-1 → Observe authentication attempts, account lockouts, and system log activity → Correlate log entries to user actions for troubleshooting and auditing purposes.
</p>

<br />

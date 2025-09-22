<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Configuring Account Policies for Active Directory</h1>
In this tutorial, you’ll learn how to configure Account Policies in Active Directory using Group Policy to enhance domain-wide security and user authentication standards. We’ll cover essential settings like Password Policy and Account Lockout Policy to help you enforce best practices across your network.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: Configuring Account Policies for Active Directory](https://youtu.be/keqxUTkp53E)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Turn on the DC-1 and Client-1 virtual machines in the Azure Portal if they are off.
- Open Group Policy Management, configure the Account Lockout Threshold to configure the account lockout threshold to 5 failed login attempts
- Go to Active Directory Users and Computers, right-click the user account, select Reset Password, and set a new secure password
- Test enabling and disabling the account to observe different login responses, then review Event Viewer logs on both DC-1 and Client-1 to analyze lockout events and security activity.

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://github.com/user-attachments/assets/793896bd-2830-4fdc-b6ad-be0a4c015888" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To set up account lockout protection, open Group Policy Management on the Domain Controller (DC-1). Navigate to the appropriate Group Policy Object (GPO), usually under Default Domain Policy, and go to Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy. There, set the Account Lockout Threshold to 5 invalid login attempts, then attempt 6 failed logins to confirm the lockout works.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/a73e391e-33c2-4fc3-860a-464e7d164d32" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To reset a user's password, open Active Directory Users and Computers on the Domain Controller. Locate and right-click the user account you want to update, then select Reset Password from the context menu. Enter a new secure password, confirm it, and optionally check the box to require the user to change it at next login.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/46b989ae-ea91-47db-9cbe-7e90fffad078" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To test account status changes, go to Active Directory Users and Computers, right-click the user account, and choose Disable Account to prevent logins. Attempt to log in with the disabled account to see the access denied message, then re-enable the account and try logging in again. 
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/cef13682-b2dc-44bb-b563-4196cd408a43" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To review security-related activity, open Event Viewer on both DC-1 and Client-1 by typing Event Viewer in the Start menu. In the Event Viewer, navigate to Windows Logs > Security to view detailed records of account lockouts, failed login attempts, and other authentication events. These logs are essential for auditing user behavior and identifying potential security issues or unauthorized access attempts. 
</p>
<br />

<p align="center">
<img src="https://github.com/user-attachments/assets/994e5afb-bec5-4370-8cdd-aa1da7c30dcb" />
</p>

<h1>Group Policy and Managing Accounts</h1>
This tutorial explores deploying an Active Directory environment, from creation and management to deactivation and removal.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory
- Powershell
- Command Prompt

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Windows Server 2022

<h2>High-Level Configuration Steps</h2>

- Dealing with Account Lockouts 
- Enabling and Disabling Accounts
- Configure Domain Password Lockout Policy
- Observing Logs

<h2>Configuration Steps</h2>

<p>
<img src="https://github.com/user-attachments/assets/fc9ae7fc-e356-4b69-b6b5-995ec2a4fd5a" />
</p>
<p>
Launch both both virtual machines to start the lab.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/a7f02275-3528-4482-b6e3-416702b5f7b1" />
</p>
<p>
Attempt to lock out the account by entering the wrong password 10 times or more while trying to gain access to Client-1.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/c9042704-8e52-49af-a1e2-19753d702a62" />
</p>
<p>
To apply the lockout policy,it has to be configured within Group Policy Management. Once in DC-1 logged in as admin, right-click on the Start menu and select Run or press command+R.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/c01ed4a4-50ea-4b70-8916-58b6c1cc8c95" />
</p>
<p>
In Run, type gpmc.msc to open up Group Policy Management.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/e4f4a752-2846-443b-ae66-1579bc6c1118" />
</p>
<p>
Once in Group Policy Management, click the drop down arrow on Forest:mydomain.com.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/090951a2-14ca-4b5d-aecd-bbdf3457b609" />
</p>
<p>
Once in Group Policy Management, click the drop down arrow on Forest:mydomain.com, click the down arrow on my domain.com, then click Default Domain Policy.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/c57d7c6f-166b-4710-9ee9-54ea20ded658" />
</p>
<p>
Click OK.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/c9a46d0d-2c79-49fd-8e00-516a8baca30b" />
</p>
<p>
Right-click on the Default Domain Policy and select Edit.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/9777ecfd-ad1f-4ac1-9062-8f462593f2d0" />
</p>
<p>
In the Group Policy Management Editor, expand Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/2a1f14af-0df7-4e84-a1ef-3f521c644225" />
</p>
<p>
Click on Account lockout duration, check the box next to "Define this policy setting" and set duration to 30 minutes.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/40584cff-a22a-4a84-b36e-23204fa84993" />
</p>
<p>
Select OK.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/076a60c2-8c2a-4302-9a80-c89c237488c7" />
</p>
<p>
Enable the Administrator account lockout and click apply and click OK.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/3736c320-7f57-4c21-8bc1-a73ac493c8ac" />
</p>
<p>
Observe the changes.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/95ad308b-0050-43f9-a8a9-51f531d93a8c" />
</p>
<p>
Go back to the Group Policy Management, navigate back to Default Domain Policy, go to Settings and scroll down to Account Policies/Account Lockout Policies and verify the changes.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/3736c320-7f57-4c21-8bc1-a73ac493c8ac" />
</p>
<p>
Login to Client-1 as jane_admin in order to force the changes using gpudate in command prompt.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/df305bb7-543e-4b7d-92fb-d16cbd865e1a" />
  <img width="2180" height="1190" alt="image" src="https://github.com/user-attachments/assets/13f52371-d708-4211-9d19-273f2ed797f9" />

</p>
<p>
Once in Client-1, open command prompt.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/868128a6-8c5f-4573-bbb2-bfcee7e406f0" />
<img width="2180" height="1190" alt="image" src="https://github.com/user-attachments/assets/84598c1a-3945-4aad-838e-48701be47931" />

</p>
<p>
Type gpupdate /force and press Enter.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/84d4f490-efe8-447c-b400-45e607c47348" />
</p>
<p>
The update has been completed successfully.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/f91bfd4a-afdd-43dc-80ed-bb752e999ee6" />
</p>
<p>
Type gpresult /r and press Enter.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/d14ceb84-c954-4db4-8cca-31573b6a1943" />
</p>
<p>
Notice that the Default Domain Policy has been applied.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/70f5d561-2940-4a4a-8da3-00d507f41b7f" />
</p>
<p>
Back in Remote Desktop, log out of Client-1 and try to lock out one of the random accounts after 5 failed attempts and notice the lock out message that appears.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/e8f46b34-7127-4cb3-a798-2a28b3b589ab" />
</p>
<p>
In DC-1, search for Active Directory Users and Computers.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/32e56d7b-eb42-4564-8e28-5d124a546b88" />
</p>
<p>
Expand mydomain.com, right-click on _EMPLOYEES and click Find.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/ad2ba64f-aa95-47e6-b747-aedca4fd9ce5" />
</p>
<p>
Type the name of the user and click on "Find Now" to locate that user. In my case it was bas.fufu
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/4c73d2f6-37b0-463b-8adf-044074ef68ad" />
</p>
<p>
Right-click on the user and select Properties. Under Account, check "Unlock Account". The account is currently locked out on the "Active Directory Domain Controller" box, select Apply and OK.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/f1fe2bc6-e537-485c-8533-27f5d1177071" />
</p>
<p>
After the account is unlocked, I logged back into Client-1 as bas.fufu and opened Command Prompt in order to verify.
</p>
<br />

<p>
<img width="1568" height="1170" alt="image" src="https://github.com/user-attachments/assets/af7d87e8-0236-489a-8de9-df9215da49c9" />
</p>
<p>
Back in DC-1, open up Active Directory Users and Computers to search bas.fufu. Right-cick and select "Reset Password".
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/70393a70-1cfc-42ba-b834-080662b37d3f" />
</p>
<p>
Enter a fresh password and make sure the "Unlock the user's account" option is also checked. Click OK.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/3d6b50d8-0aaa-4d55-ac36-94a211551f6c" />
</p>
<p>
Disconnect and log back in as bas.fufu in Client-1.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/70393a70-1cfc-42ba-b834-080662b37d3f" />
</p>
<p>
Login was successful.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/23d03492-bb08-49a5-8b29-07de0181ef39" />
</p>
<p>
Login was successful.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/ff602db5-5416-4927-b7ef-78634831050d" />
</p>
<p>
Once inside client-1 as bas.fufu, search "eventvwr.msc".
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/68ebe082-4545-4968-b95c-ee528735dcc7" />
</p>
<p>
Cannot access the query because it needs administrator rights.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/1c96bda9-45c4-4fa7-b069-b5b3243d1149" />
</p>
<p>
Search for eventvwr.msc, right-click and "Run as Administrator".
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/95cff7a2-3074-4cdb-b259-f6476e97bee7" />
</p>
<p>
Login as Jane Smith to gain administrative rights
</p>
<br />

<p>
<img width="2376" height="1570" alt="image" src="https://github.com/user-attachments/assets/70c2474b-61c9-49e0-a72e-bc2d64a3abb6" />
</p>
<p>
Go to Security after expanding Windows Logs, click it then right-click and choose Find.
</p>
<br />

<p>
<img src="https://github.com/user-attachments/assets/dcf617c5-2b08-4b9c-97a0-cdd9590d38c3" />
</p>
<p>
To conclude this lab, observe the failed attempts to login as bas.fufu.
</p>
<br />

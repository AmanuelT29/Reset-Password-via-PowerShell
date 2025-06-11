<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/2/2f/PowerShell_5.0_icon.png" alt="PowerShell Logo" width="150"/>
</p>


# Reset User Passwords via PowerShell

## Platform and Tools Used

## Objective

In this small project, I will demonstrate how to reset a user password using PowerShell. I will take on the role of an admin named Phillip and reset the password for a user named Sophie.

The process involves two main steps:

**1.** Creating a new (temporary) password.

**2.** Enforcing a password reset at the next logon, so that when Sophie logs in with the temporary password, she is required to create a new one before accessing her computer.

-----

### Step 1: Create a new (Temporary) Password
- To create a temporary password, I ran the following command:
`Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose`

<img src="https://github.com/user-attachments/assets/37918f53-f631-40d7-8cad-8c45f64db001" alt="Screenshot" width="700"/>

- After I ran the command, I was prompted to enter a new password. I reset the password to **Basketball23$**, then pressed Enter again to apply the changes.


### Step 2: Enforce a password reset at the next logon
- To ensure Sophie doesn’t continue using a password we know, we can force a password reset at her next logon with the following command:
`Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose` then press enter to apply the changes.

 <img src="https://github.com/user-attachments/assets/8ccc3e7a-f473-4ee3-862a-c5d2ba588d4d" alt="Screenshot" width="700"/>

### Verify the Changes Applied

- To confirm that the changes have been applied, I will show Sophie’s perspective as she tries to log in using the temporary password **Basketball23$**:
  
<img src="https://github.com/user-attachments/assets/0d7b142e-b7c0-4a68-a5be-4cbbfe128ece" alt="Login Screenshot 1" width="300"/>
<img src="https://github.com/user-attachments/assets/4cfc0462-377c-4b4b-ad71-2d7384e9710f" alt="Login Screenshot 2" width="300"/>

As shown in the screenshot, when Sophie tried to log in using the temporary password, she was prompted to create a new password before signing in.

- New Password:

<img src="https://github.com/user-attachments/assets/6e12f277-b4d9-46fb-aae6-a8ebafd48b3f" alt="New Password Prompt" width="350"/>
<img src="https://github.com/user-attachments/assets/cdba9eac-8bf9-4a8b-b222-47d8ac3a3b7a" alt="Password Confirmation" width="350"/>

As shown in the screenshot, Sophie now creates a new password **Football23$** to log in.

- Password successfully changed:
  
  <img src="https://github.com/user-attachments/assets/a9b55dc4-66be-442f-b3b8-c923425a5d50" alt="Password Changed Confirmation" width="400"/>

  As shown in the screenshot, the password has been successfully changed. Sophie now has access to her computer again.


  

  


 
  




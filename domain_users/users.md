# Creating & Joining Domain Users

## Summary (PowerShell Disclaimer)

**** For this lab section, going create users, then join those users to a domain controller. ****

**** This section will user PowerShell. So, it's important that you understand scripting, or at least you are comfortable working with the terminal. ****

**** IT professionals use scripts for various tasks. And so, getting comfortable with scripts will benefit you in your profession. ****

**** Let's jump in ****



* ### Storing a Password in the environment Variable
For security reasons, it's not advisable to store passwords as plainText.
Therefore, we will create a environment variable and then store that password in that variable. To do this, see below:

- Launch PowerShell and Run it as Administrator
- In your terminal type in the following script then press enter:
    - ```bash
        $password = Read-Host "Enter User Password:" -AsSecureString
- In the prompt, enter a default password for your user. For example:
    - ```bash
        P@ssword


* ### Creating a new User
The Following script will create a new user, assign a user name, assign the default password from the environment variable we created, and then add the user to the Users Organizational Unit.

- In your terminal type the following (Change the values, such as domain and user information to match your own) script and then press enter:
    - ```bash
        New ADUser -SamAccountName "jane.smith" -Name "Jane Smith" -GivenName "Jane" -Surname "Smith" -UserPrincipalName "jane.smith@sparksdc.com" -Password $password -Path "OU=Users,DC=sparksdc,DC=com"
- Verify that your user exists with the following:
    - ```bash
        GET-AdGroupMember -Identity "Users"
- Troubleshoot any issues as needed

* ### Creating a new User
The Following script will mandate a user to create a new password when they logon. To this, we will need to import a AD Module. 

- In your terminal type the following (Use the name of the user you created) scripts and then press enter:

    - Import Active Directory Module (Then press enter):
        - ```bash
            Import-Module ActiveDirectory


    - Change Password on logon (Then press enter):
        - ```bash
            Set-AdUser -Identity "jane.smith" -UserMustChangePassword $true

- Troubleshoot any issues as needed
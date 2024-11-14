# Creating Users

## Summary (PowerShell Disclaimer)

**** For this lab section, going create users, then join those users to a domain controller. ****

**** This section will user PowerShell. So, it's important that you understand scripting, or at least you are comfortable working with the terminal. ****

**** IT professionals use scripts for various tasks. And so, getting comfortable with scripts will benefit you in your profession. ****

**** Let's jump in ****



* ### Storing a Password in the environment Variable
For security reasons, it's not recommended to store passwords as plainText.
Therefore, we will create a environment variable and then store that password in that variable. To do this, see below:

- Launch PowerShell and Run it as Administrator
- In your terminal type in the following script then press enter:
    - ```powershell
        $password = Read-Host "Enter User Password:" -AsSecureString
- In the prompt, enter a default password for your user. For example:
    - ```powershell
        P@ssword


    ![Read-Host_Password](https://github.com/user-attachments/assets/364258d9-989c-4d3d-bf34-442b0a8d8ac4)


* ### Creating a new User
The Following script will create a new user, assign a user name, assign the default password from the environment variable we created, and then add the user to the Users Organizational Unit.

- In your terminal type the following (Change the values, such as domain and user information to match your own) script and then press enter:


    - ```powershell
        New-ADOrganizationalUnit -Name "MyUsers" -Path "DC=sparksdc, DC=com"


    - ```powershell
        New-ADUser -SamAccountName "jane.smith" -Name "Jane Smith" -GivenName "Jane" -Surname "Smith" -UserPrincipalName "jane.smith@sparksdc.com" -AccountPassword $password -Path "OU=MyUsers,DC=sparksdc,DC=com"

- Verify that your user exists with the following:

    - ```powershell
        GET-ADUser -Filter * -SearchBase "OU=MyUsers,DC=sparksdc,DC=com"


- Troubleshoot any issues as needed

* ### Change password Policy
The Following script will mandate a user to create a new password when they logon. To this, we will need to import a AD Module. 

- In your terminal type the following (Use the name of the user you created) scripts and then press enter:

    - Import Active Directory Module (Then press enter):
        - ```powershell
            Import-Module ActiveDirectory

    - Verify that a User Exists
        - ````powershell
            GET-ADUser -Identity "jane,smith"

    - Change Password on logon (Then press enter):
        - ```powershell
            Set-AdUser -Identity "jane.smith" -ChangePasswordAtLogon $true


* ### Enable Users
The Following script will enable a user we created so they can be able to login and join AD. 

- In your terminal type the following (Use the name of the user you created) scripts and then press enter:

    - Enable User:
        - ```powershell
            Enable-ADAccount -Identity "jane.smith"


        ![Enable_User](https://github.com/user-attachments/assets/114777c9-a4be-412e-aaec-e73d75edffc1)


    - Verify your changes
        - ```powershell
            GET-ADUser -Identity "jane.smith"

        ![Verify_OU_User](https://github.com/user-attachments/assets/6d4d9b10-47c5-43fa-885d-4ef7ccd58ae1)


- Troubleshoot any issues as needed

*** You can create as many users as you want. It may be good practice to create a few more users to get familiar with PowerShell ***

## The next phase is to join a client machine to a domain. Head over to <a href="https://github.com/KwaneleKhumalo/active_directory/blob/master/join_domain/join.md" target="_blank">Joining a Domain</a>!


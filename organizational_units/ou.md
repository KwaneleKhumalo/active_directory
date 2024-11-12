# Active Directory Organizational Units (OU)

**** For this lab, we're just going to setup 2 or 3 Organizational Units. ****

## Creating OU, and an Admin Account

* ### Creating OU, and an Admin Account
    - Launch Server Manager
    - Select Tools, then Choose Active Directory Users and Computers as shown below
 

![Launch_Users_Computers](https://github.com/user-attachments/assets/23be1c9a-2f0f-4a88-b2d0-014cb75607d2)

    

    - Select your domain, right-click, select 'new' then Select Organizational Unit
    - Type in the name of your of your OU (Administrators, Users, etc.) and click 'OK'
    - Your newly created Admin account will show on the right pane.



https://github.com/user-attachments/assets/fd4546a2-7d95-4a2f-bceb-630bc0a6f356






    - Next, we need to make this account a 'Member Of' admins. To do so, see below:
 
    






https://github.com/user-attachments/assets/633231ab-71ff-48af-90fd-66d3b5b82a05




* ### Testing the new Admin Account
    - Sign-out of the current account
    - On the login screen, Select "Other user"
    - Enter the new Admin Account Credentials
        - Mine is sparks.sparky
    - If you followed the steps correctly, you will be welcomed by a new desktop.
        - Troubleshoot any issues if needed.
     

        ![Admin_Logon](https://github.com/user-attachments/assets/ff4c0067-2e3c-48c3-a42c-60dafe06af8c)


## Great! The next phase is to create domain users with PowerShell. Head over to <a href="https://github.com/KwaneleKhumalo/active_directory/blob/master/domain_users/users.md" target="_blank">Domain Users</a>!



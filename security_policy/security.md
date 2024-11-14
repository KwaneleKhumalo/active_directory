# Configuring Basic Security Policies

## Summary

*** For this lab section, we are going to implement a few basic security policies in Active Directory Using Powershell. ***

*** The approach I Am taking here can also be similar to Group Policy Objects. ALWAYS check Powershell Documentation. At the time of writing, I realized that their documentation has changed from previous years. So, it's important to check their current documentation. I included the link at the end. ***

1. Implement Strong Password
2. Account Lockout


*** Launch Powershell (Run as Admin) in your Windows Server machine, and let's jump in ***

1. Implement Strong Passwords
    - Import Active Directory
        - ```powershell
            #Powershell
            Import-Module ActiveDirectory #Import the AD Module

            #Strong Password and Account Lockout
            Set-AdDefaultDomainPasswordPolicy -Identity "sparksdc.com" -LockoutThreshold 3 -LockoutDuration "00:30:00" -MinPasswordLength 10 -MinPasswordAge 90 -MaxPasswordAge 180 -PasswordHistoryCount 10 -ComplexityEnabled $true

    - Test out the newly deployed password policy
        - Go to your client machine and enter a wrong password a few times. The account should lock.
        - You will have 30 minutes again to retry the password attempt.
        - You may also add another account and test out the "Complexity" of the password.

    
# Please see Powershell Documentation for more information on Parameters.


 <a href="https://learn.microsoft.com/en-us/powershell/module/activedirectory/set-adfinegrainedpasswordpolicy?view=windowsserver2022-ps" target="_blank">Powershell Documentation</a>


*** Thank you for checking out this project. Please feel free to provide me with any feedback. This lab can be expanded. I have more labs to migrate to my github account, so stay tuned for those as well!  ***


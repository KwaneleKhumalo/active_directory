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
- In your terminal add the following script:
    - ```bash
        $password = Read-Host "Enter User Password:" -AsSecureString

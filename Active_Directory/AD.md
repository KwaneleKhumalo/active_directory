# Active Directory Installation and Setup Guide

## Computer Renaming & AD Installation

* ### Computer Renaming
    - Launch Server Manager (Search for this in your start menu)
    - On the Left Pane, select Local Server
    - Select 'Computer Name' Link
    - Select 'Change' in a pop-up window
    - Type in the name of your Domain Controller
    - Restart your VM after completion
    - See Demo Below:



* ### Installing Active Directory Domain Services (ADDS)
    - Top-Right corner, Select 'Manage' from the menu items
    - Select 'Add Roles and Features' option
    - Accept selections on the first 2 steps ('Before You Begin' & 'Installation Type)
    - Under 'Server Selection', select your Domain Controller (DC)
    - Under Server Roles, Select 'Active Directory Domain Services'
        - Select 'Add features' in the popup
    - Accept the rest of the default selected options, click next
    - Select 'Install' in the 'Confirmation' section to begin the installation
    - See Demo Below






* ### ADDS Deployment
    - Top-Right corner, Select the Yellow Flag from the menu items
    - Select 'Promote this server to a domain controller' option
    - Select 'Add a new forest' in the Deployment Configuration pop-up
    - Name your Root domain, click next
        - This can be any name ending with a domain (.com)
    - Choose Password under the 'Domain Controller Options', click next
    - Accept the rest of the default selected options, then install
    - Select 'Install' in the 'Confirmation' section to begin the installation
    - You will be signed out after the installation is complete and the system will restart to apply the settings
    - See Demo below:






## Great! You have installed your ADDS. Next Step is working with OUs. Head over to <a href="https://github.com/KwaneleKhumalo/active_directory/blob/master/orgaizational_units/ou.md" target="_blank">Organizational Units</a>!





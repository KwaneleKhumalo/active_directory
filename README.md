# Active Directory Project: Home Lab 2024

## Summary

Active Directory (AD) is a Microsoft directory service designed to centralize the management of network resources across defined domains. It stores information about users, computers, and other network objects in a structured database, making it easier for administrators to manage and secure their network.

This lab provides snapshot process of setting up a virtual lab environment using VirtualBox, installing Windows Server and Windows 10, configuring a domain network, installing Active Directory, joining domain devices, Working with Powershell, and more.


## Key Components of AD that we focus on:

* #### Domain
    - A group of objects (users, computers, devices, etc) sharing the same AD Database (DB).
* #### Domain Controller (DC)
    - A Server that hosts AD and handles authentication behaviors.
* #### Organizational Units (OU)
    -  Containers which hold domain objects (users, groups, computers). OUs are helpful for managing and organizing domain objects.
* #### Users & Groups
    - Represents Accounts (Or personnel) and groups refer to a collection of users and devices managed by at least one (preferable) entity. We will demonstrate how to create users and groups and apply certain permissions to various groups
* #### Group Policy
    - Enforcement of various settings (Security, software installation, system configuration) for different groups and users.


## Pre-Requisites

* Networking Fundamentals
* Virtualization
* Windows Server
* Computer and Basic Troubleshooting skills

# File Structure

1. ## Setup
    - Setting up the Virtual Environment along with other Virtual Machines
2. ## Network
    - Configuring Virtual Network Cards
    - Configuring IP Address Information 
    - Configuring Network Adapters
3. ## Active Directory
    - Installing Active Directory
    - Configuring Active Directory
    - Deploy Active Directory
4. ## Organizational Units
    - Creating an Organizational Unit
    - Configure OU Management
5. ## Domain Users
    - Getting Started with Powershell
    - Creating Users with Powershell
    - Creating OU with Powershell
    - Working with Environment Variables within Powershell
    - Add a user to a OU
    - Enforce password change on logon for a user
6. ## Join Domain
    - Add Adapter 2 to Client Machine
    - Configure client machine using Powershell
    - Configure Networks for the client machine
    - Join the client machine to a domain
7. ## Security
    - Configure Password security with Powershell. 



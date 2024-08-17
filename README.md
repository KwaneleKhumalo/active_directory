# Active Directory Project: Home Lab 2024
(Still in progress)

## Introduction

Active Directory (AD) is a Microsoft Database service developed to centralize the management or an organization's network resources across defined domains. It stores data as objects, making it intuitive for administrators and users to find and use. 

This lab will demonstrate the process of setting up the lab environment using Virtual Box, installation of Microsoft's Windows Server and Windows 10. We will then demonstrate how to setup a domain network, install AD, Join the AD and much more. 

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

* ## Setup
    - Installation Guide
    - Downloading and Installing VirtualBox
    - Configuring Nat Networks
    - Server/Domain Installation and Setup
    - Windows Client Installation

* ## AD Installation and Setup
    - AD Installation
    - Setup AD Domain Services.
    - Setup a Domain Tree



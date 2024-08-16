# Lab Setup, Tools & Configuration

## Lab Setup

* ### Download & Install VirtualBox for your host machine
    - Download VirtualBox Here: <a href="https://www.virtualbox.org/wiki/Downloads" target="_blank">VirtualBox Website</a>

    - Run and Complete the Installation

* ### Configure VirtualBox Network Settings
    - Launch VirtualBox and get follow the configuration steps below:

1. #### Go to File > Tools > Network Manager
    - This will help us configure Networks

        ![Network Manager Img](../images/Nat.png)

2. #### Select the 'NAT Networks' tab on the right pane
    - Click the 'Create' button at the top to create a new Network

    - Give your Network a Name

    - Set your Network CIDR: (example: 10.0.2.0/24)
        - This range will assign IPs from '10.0.2.1' to '10.0.2.254'.
    
        ![VirtualBox IP Setup](../images/VB_IP.png)

3. #### Click 'Apply' at the bottom right to accept the changes


## Windows Server Setup

* ### Windows Server Download & Installation
    - Download Windows Server [ISO FILE] Here: [Win 2022 Download Website](https://info.microsoft.com/ww-landing-windows-server-2022.html)

    - ***The download can take time depending on your machine's resources, so plan accordingly.***

    - Follow the installation guide below: 

        1. Create a New CM:

         



# Lab Setup, Tools & Configuration

## Lab Setup

* ### Download & Install VirtualBox for your host machine
    - Download VirtualBox Here: <a href="https://www.virtualbox.org/wiki/Downloads" target="_blank">VirtualBox Website</a>

    - Run and Complete the Installation

* ### Configure VirtualBox Network Settings
    - Launch VirtualBox and get follow the configuration steps below:

1. #### Go to File > Tools > Network Manager
        ![Network Manager Img](../images/Nat.png)

2. #### Select the 'NAT Networks' tab on the right pane
    - Click the 'Create' button at the top to create a new Network

    - Give your Network a Name

    - Set your Network CIDR: (example: 10.0.2.0/24)
        - This range will assign IPs from '10.0.2.1' to '10.0.2.254'.
    
        ![VirtualBox IP Setup](../images/VB_IP.png)

3. #### Click 'Apply' at the bottom right to accept the changes

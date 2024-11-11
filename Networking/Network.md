# Network Configuration

## Active_Directory Network Setup

* ### Run the newly installed Windows Server
    - Launch the Command Prompt as 'Administrator'
    -  Run the following snippet to check the current IP configuration
        - ```bash   ipconfig
    - Next, ping 'google.com' to check network connection (troubleshoot any issues if you're not getting desired responses from the ping)
    - If everything is as expected, turn off your server machine and move on to adding another Network adapter. See the following step ('Configuring Server Network)

* ### Configure Server Network
    - In VirtualBox, Select your Server VM
    -  Select 'Settings' from the menu items
    - Select 'Network' from the given Options
        - Adapter 1 (Provide access to public network) should have a Nat network we configured
        - Select Adapter 2 (Internal network only)
        - Select the 'Enable Adapter Network' Checkbox to enable this network
        - Attach to: Select 'Internal Network'
        - Name: Leave Default ('intnet')
    - Apply your changes and Start your VM again
    - (Optional) Rename each adapter in the Network Connections to public facing network from a private-internal network
    - run 'ipconfig /all' to confirm both your adapters are configured
    - Quick visual demo below:
 




https://github.com/user-attachments/assets/c5b5dc97-38ff-4d8a-88af-fd8229c4882f




      

* ### Configure and Assign IPv4 to Internal Network
    - Launch Control Panel
    - Select 'Network and Sharing Center'
    - On the Left Pane, select 'Change Adapter Settings'
    - Open Properties of the Internal Network
    - From the list, disable IPv6 (We will be using IPv4)
    - Select IPv4 and open its properties
    - In the Properties, select 'Use the following IP address' and add details below:
        - IP Address: 172.20.0.1
        - Subnet Mask: 255.255.255.0
        - Default Gateway: < Leave Blank >

    - Select, 'Use the following DNS server addresses' and add details below:
        - Preferred DNS server: 127.0.0.1
        - Alternative DNS server: < Leave Blank >

    - Apply all your changes and close Networking window
    - See Short Demo Below:

https://github.com/user-attachments/assets/9554bf8d-d0b4-4980-9a95-6c79fd441c4b

- Launch command line and run 'ipconfig' to verify changes to your internal network. Troubleshoot issues if needed. 

## Sweet!! We have configured our Network! Next, we're going to <a href="https://github.com/KwaneleKhumalo/active_directory/blob/master/Active_Directory/AD.md" target="_blank">Active Directory</a>!
    



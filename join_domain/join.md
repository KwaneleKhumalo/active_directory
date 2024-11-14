# Joining a Domain with Powershell

## Summary

**** For this lab section, we're going to login to our Windows 10 (Jane's VM) Workgroup Machines, then join the domain server. All the work in this section will be completed using powershell. ****

*** Before we start joining a domain, we first need to make sure that our Clien't machine is connected to the same network as our server. Based on our setup, this is not the case intentionally. So currently, our client machine should be connected to Adapter 1 (NAT Network) ONLY. ***

*** In this section, we're going change a lot! ***

**** Let's jump in ****

* ### Connecting Adapter 2 (Internal Network)
Our Domain has 2 Networks, Adapter 1 (Public) and Adapter 2 (Internal). In order for our client to communicate with our Domain, we will need both our machines to be on the same network. Therefore, we will configure a second adapter, then modify some things to get the client machine on the same IP range as our domain.

Currently, if you ping your domain IP address, you should be receiving "timeout" packet response. We are going to solve this issue below:

- Turn off your client machine
- In VirtualBox, go to Windows 10 Network Settings and enable Adapter 2
- Make sure the "Attached to" is the same as your server:
    - Attached to: Internal Network
    - Name: intnet (default)
- Start your client Machine
- Go to your Network sharing and verify that you have 2 adapters. You may rename these as we did on our server.

* ### Configure IPv4 Address
Before starting. Make sure your client machine shows two Network Adapters (1 and 2) as stated above.


- Check our IP configuration. Run the following
    - ```powershell
        ipconfig
        #Verify both adapters are present with different IP addresses.

- Check Network Adapter values
    - ```powershell
        #For this section, we need the ifIndex number of our Internal Network
        Get-NetAdapter

- Assign a new IPv4 address to Internal Network
    - ```powershell
        New-NetIPAddress -InterfaceIndex 14 -IPAdress 172.20.0.2 -PrefixLength 24
        # New-NetIPAddress: Assignining a new Network IP Address
        # InterfaceIndex: This is from the ifIndex from Get-NetAdapter
        # IPAddress: The IP Address we're configuring
        # -PrefixLength: Subnet Mask. This is the same as our Domain (Important)

- Verify newly configured IP Address
    - ```powershell
        ipconfig

- Ping Server to get a response
    - ```powershell
        ping 172.20.0.1
        #if you configured everything correctly, you should receive a response from the server. If not, this is a perfect time to exercise your analytical and troubleshooting skills. 


* ### Joining a Domain

So far, we have all the requirements to join the client machine to a domain controller. The following step will finalize this process. We are still doing this work in Powershell with administrative privileges.  

- Rename the client computer

    - ```powershell
        # We Need to rename our PC so we can distinguish it 
        Rename-Computer -NewName Jane-Smith-PC
        # Restart the PC to apply the changes
        Restart-Computer
    
    - After the PC has restarted. Go to the About PC and verify that the changes have been applied.

- Join the domain

    - ```powershell
        #Join a domain and then restart the pc to apply changes
        Add-Computer -DomainName sparksdc.com -Restart
        #You will be prompted to enter your Domain Admin Password.

    - Possible Error message you may get:
        - "The specified domain either does not exist or could not be contacted"
        - Possible Solutions below:
            - ```powershell
                #Flush the DNS cache by running the following cmd
                ipconfig /flushdns
            - In the internal Network settings, modify the dns to be the Server IP Address

- Troubleshoot other issues as needed.

        
# Joining a Domain with Powershell

## Summary

*** For this lab section, we're going to login to our Windows 10 (Jane's VM) Workgroup Machines, then join the domain server. All the work in this section will be completed using powershell. ***

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

![Clien_2_Adapters](https://github.com/user-attachments/assets/055c7915-03ae-4f78-9740-7876c22b51a8)


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

![Get-Adapter](https://github.com/user-attachments/assets/cfb40635-09ce-4ad2-90cc-4e8bc252ea33)


- Assign a new IPv4 address to Internal Network
    - ```powershell
        New-NetIPAddress -InterfaceIndex 14 -IPAdress 172.20.0.2 -PrefixLength 24
        # New-NetIPAddress: Assignining a new Network IP Address
        # InterfaceIndex: This is from the ifIndex from Get-NetAdapter
        # IPAddress: The IP Address we're configuring
        # -PrefixLength: Subnet Mask. This is the same as our Domain (Important)


    ![New_IP](https://github.com/user-attachments/assets/c6eec0f2-0406-4448-b091-8e3f6dfc74d7)


- Verify newly configured IP Address
    - ```powershell
        ipconfig

![ipConfig_Powershell](https://github.com/user-attachments/assets/810d2f3f-51bd-480f-818b-6e426b178673)


- Ping Server to get a response
    - ```powershell
        ping 172.20.0.1
        #if you configured everything correctly, you should receive a response from the server. If not, this is a perfect time to exercise your analytical and troubleshooting skills.

    
![ping_server](https://github.com/user-attachments/assets/11b00203-a14c-45a2-adc6-88c1a40f9462)


* ### Joining a Domain

So far, we have all the requirements to join the client machine to a domain controller. The following step will finalize this process. We are still doing this work in Powershell with administrative privileges.  

- Rename the client computer

    - ```powershell
        # We Need to rename our PC so we can distinguish it 
        Rename-Computer -NewName Jane-Smith-PC
        # Restart the PC to apply the changes
        Restart-Computer


    ![Change_PC_Name](https://github.com/user-attachments/assets/7c89aa6b-3e3e-4411-9956-bc0f07105c0a)

    
    - After the PC has restarted. Go to the About PC and verify that the changes have been applied.

- Join the domain

    - ```powershell
        #Join a domain and then restart the pc to apply changes
        Add-Computer -DomainName sparksdc.com -Restart
        #You will be prompted to enter your Domain Admin Password.


![Join_Domain](https://github.com/user-attachments/assets/218da14f-96ac-453b-a33e-8278d5e07f6d)

    
- Possible Error message you may get:
    - "The specified domain either does not exist or could not be contacted"
        - Possible Solutions below:
            - ```powershell
                #Flush the DNS cache by running the following cmd
                ipconfig /flushdns
            - In the internal Network settings, modify the dns to be the Server IP Address

- Troubleshoot other issues as needed.

## The next phase is to create a few group policies for our environment. Head over to <a href="https://github.com/KwaneleKhumalo/active_directory/blob/master/security_policy/group_policy.md" target="_blank">Security Policy</a>!

        

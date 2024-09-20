# Using Routing to Connect Two LANs

## Add a Router to our LAN

1. Click on _Network Devices_ category
2. Click on _Routers_ sub category
3. Click on _4331_ router and add to our LAN
4. Select _Copper Straight Through_ from connections
5. Connect _Gigabit Ethernet 0/1_ on the Switch to _Gigabit Ethernet 0/0/0_ on the router

![Finding a Router](<../../.gitbook/assets/image (26).png>)

![Physically Connect Router](<../../.gitbook/assets/image (28).png>)

## Assign Router IP addresses for our LAN

1. Click on the _Router_ to bring up it's _Physical Config_.
2. Click on the _Config_ tab
3. Select the _Gigabit Ethernet 0/0/0_ interface from the set of modules
4. You will need to **turn the port on**, there is a check box
5. Give this interface an _IP address_ of **192.168.0.1**, subnet mask should auto populate.
6. Close the config screen
7. Once the network interface is showing green icons, use **Add Simple PDU** to test connectivity between either PC and the Router.

![Physical Router Config](<../../.gitbook/assets/image (29).png>)

![Configure Gigabit Ethernet 0/0/0 on Router](<../../.gitbook/assets/image (30).png>)

![LAN with Router](<../../.gitbook/assets/image (32).png>)

![Test Router to PC](<../../.gitbook/assets/image (33).png>)

## Build a Second LAN

Now you need to build an entire second LAN. Fortunately you can copy paste the first LAN using the following steps.

1. Click on the Selection tool in the toolbar.
2. Select the whole first LAN
3. Use Ctrl C (or CMD C on mac) and Ctrl V (CMD V) to copy and paste

![Selection Tool](<../../.gitbook/assets/image (34).png>)

![Select LAN](<../../.gitbook/assets/image (35).png>)

![Pasted Second LAN](<../../.gitbook/assets/image (36).png>)

## Setup second LAN IP Addresses

We wish to be able to route packets from a PC in one LAN, to a PC on the other LAN. For this they will have to have distinct sets of IP addresses.

1. Change the IP addresses of the PCs and Router in LAN 2 to **192.168.1.xxx**.
2. Make sure you are selecting the correct interface when you configure each device.

## Setup Connection between Two Routers

1. Use _Copper Straight Through_ to connect the following two interfaces
   1. Router 1 Gigabit Ethernet 0/0/1
   2. Router 2 Gigabit Ethernet 0/0/1
2. Use the config screen to set the IP addresses as shown in table (some of them should already be done)
3. Make sure you **turn each interface** on using the checkbox
4. Use **Add Simple PDU** to test connectivity from one router to another.

| Device       | Interface              | IP Address  | Subnet Mask   |
| ------------ | ---------------------- | ----------- | ------------- |
| Router LAN 1 | Gigabit Ethernet 0/0/0 | 192.168.0.1 | 255.255.255.0 |
| Router LAN 1 | Gigabit Ethernet 0/0/1 | 10.0.0.1    | 255.0.0.0     |
| Router LAN 2 | Gigabit Ethernet 0/0/0 | 192.168.1.1 | 255.255.255.0 |
| Router LAN 2 | Gigabit Ethernet 0/0/1 | 10.0.0.2    | 255.0.0.0     |

![Routers connected to each other](<../../.gitbook/assets/image (37).png>)

## Setup Static Routing on Routers

1. Click on the Router for LAN 1
2. Click on _Config_ tab.
3. Click on _Routing -> Static_ sub module
4. Enter details of LAN 2
   1. Network 192.168.1.0
   2. Subnet Mask 255.255.255.0
   3. Next Hop 10.0.0.2
5. Click on Add to add it to routing table
6. Close the Config screen
7. Repeat for the other router, but now setting up the details to go the other way
   1. Network 192.168.0.0
   2. Subnet Mask 255.255.255.0
   3. Next Hop 10.0.0.1

![Setup Static Routing](<../../.gitbook/assets/image (39).png>)

## Setup Default Gateway on PCs

If a PC wishes to send a message to an IP on a different LAN, it needs to be told where to send those messages. This is the _Default Gateway_ for that PC.

1. Click on a PC in LAN 1
2. Click on the _Config_ tab.
3. Click on the _Global -> Settings_ module.
4. Enter the IP address of the Router **192.168.0.1** into the _Default Gateway_.
5. Repeat for the other PC
6. Repeat for each PC in the other LAN, but the Router IP will now be **192.168.1.1**.
7. Give the network time to settle, then try **Add Simple PDU** from a PC on one network to another.
8. Sometimes you need to test Simple PDUs from each PC to their own router, then to the other router, then finally a PC on the other LAN.

![](<../../.gitbook/assets/image (40).png>)

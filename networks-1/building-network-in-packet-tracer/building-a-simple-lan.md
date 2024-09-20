# Building a Simple LAN

## Place a Switch on the Network

* Click on _Network Device_ category
* Click on _Switch_ sub category
* Place a _2960_ switch onto the network

![Placing a Switch](<../../.gitbook/assets/image (14).png>)

## Place Two PCs on the Network

1. Click on _End Device_ category
2. Click on _End Device_ sub category
3. Place two PCs onto the network

![Placing Two PCs](<../../.gitbook/assets/image (15).png>)

## Physically Connect PCs to the Switch

1. Select _Connections_ category
2. Select _Connections_ sub category (likely selected by default)
3. Select _Copper Straight Through_ from devices
4. Click on one of the PCs
5. Select _Fast Ethernet 0_
6. Click on the Switch
7. Select one of the _Fast Ethernet \<x>_ ports

![Select Copper Straight Through](<../../.gitbook/assets/image (16).png>)

![Connect to PC](<../../.gitbook/assets/image (17).png>)

![Connect to Switch](<../../.gitbook/assets/image (18).png>)

![Physical Connections Made](<../../.gitbook/assets/image (19).png>)

## Setup Static IP addresses on PCs

1. Click on the PC to bring up it's _Physical_ configuration page
2. Click on _Config_ tab
3. Select the _Fast Ethernet 0_ interface
4. Enter an IP address **192.168.0.2** for the first PC
5. Click into the _subnet mask_ and it should auto populate
6. Close the config sub window
7. Hover mouse over that PC and check the config tooltip. It should show the IP address
8. Repeat for the other PC, but set the ip to **192.168.0.3**.

![PC Physical Config](<../../.gitbook/assets/image (20).png>)

![Setup Static IP address](<../../.gitbook/assets/image (21).png>)

![Check IP address in PC tooltip](<../../.gitbook/assets/image (22).png>)

## Test the Network Connection using Send PDU

We will now check network connectivity between our two PCs by sending a PDU (Protocol Data Unit). This will send a ping from one machine to another and back.

1. Select _Add Simple PDU_ from the top toolbar
2. Click on one of the PCs, it should leave an envelop on it
3. Click on the other PC, and it should attempt the ping
4. Check the PDU success in the bottom right panel.

![Select Add Simple PDU](<../../.gitbook/assets/image (23).png>)

![Select Source for PDU](<../../.gitbook/assets/image (24).png>)

![Check PDU success](<../../.gitbook/assets/image (25).png>)

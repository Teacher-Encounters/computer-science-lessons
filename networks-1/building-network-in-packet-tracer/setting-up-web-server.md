# Setting up Web Server

This tutorial will assume you have built a simple LAN. The PC's already have the following configuration.

![Starting LAN](<../../.gitbook/assets/image (41).png>)

| Device | IP Address  |
| ------ | ----------- |
| PC 1   | 192.168.0.2 |
| PC 2   | 192.168.0.3 |

## Add a Server

1. Click on _End Devices_ category
2. Click on _End Devices_ sub category
3. Click on _Server_ and drag it onto your network

![Add Server](<../../.gitbook/assets/image (42).png>)

## Configure and Connect Server

1. Click on the server to bring up its _Physical Config_ window
2. Click on the _Config_ tab
3. Click on the _Fast Ethernet 0_ module
4. Enter IP address of 192.168.0.250
5. Click into Subnet mask, it should populate automatically
6. Close the config screen
7. Use _Copper Straight Through_ to connect one of the _Fast Ethernet \<x>_ ports on the _Switch_ to _Fast Ethernet 0_ on the _Server_.

![Server Physical Config](<../../.gitbook/assets/image (43).png>)

![Server Module Config](<../../.gitbook/assets/image (44).png>)

![Server Connect Fast Ethernet](<../../.gitbook/assets/image (45).png>)

## Setup HTTP server

1. Click on the _Server_ to open the server config window
2. Click on the _Services_ tab
3. Click on the _HTTP_ service module - from here you can configure the web server, it should be on by default. You can edit the contents of the html, css and javascript files being served from here.
4. Close the server config window.
5. Click on one of the PCs to open their config window
6. Click on the _Desktop_ tab
7. Click on the _Web Browser_.
8. Type the IP address of the server into the address bar **192.168.0.250**.
9. Click on _Go_ and you should be presented with the web page being served.

![HTTP Server Config](<../../.gitbook/assets/image (46).png>)

![PC Desktop](<../../.gitbook/assets/image (47).png>)

![Visiting a Web Page](<../../.gitbook/assets/image (48).png>)

## Setup DNS on Server

One of the key protocols you need to understand is the Domain Name Service/System (DNS).

It is the method by which we can visit urls like bbc.co.uk, rather than having to know the IP addresses of all our favourite sites.

1. Click on the Server to open the Config window.
2. Click on _Services_ to open the service tab
3. Click on _DNS_ to configure the Domain Name Service
4. Turn DNS on
5. Create a domain for this web server, I will use **mysite.com**. Type that into the _Name_ field.
6. Type the IP address of this web server into the _Address_ box.
7. Click on _Add_ to add the A Record for that site.

![Enter 'A Record' details](<../../.gitbook/assets/image (49).png>)

!['A Record' created](<../../.gitbook/assets/image (50).png>)

## Setup DNS on PCs

Now that we have a DNS running on the server, we need to tell each PC. This can be part of the DHCP setup, but since we are doing things manually, we will need to tell each PC about our DNS.

1. Click on a PC
2. Click on the _Config_ tab
3. Click on _Settings_ module
4. Enter DNS IP address of **192.168.0.250** into the DNS box.
5. Click on the _Desktop_ tab
6. Open the _Web Browser_.
7. Try to visit **mysite.com** in the web browser and it should open the same page as before

![Setup DNS on PC](<../../.gitbook/assets/image (51).png>)

![Visit Web page using DNS](<../../.gitbook/assets/image (52).png>)

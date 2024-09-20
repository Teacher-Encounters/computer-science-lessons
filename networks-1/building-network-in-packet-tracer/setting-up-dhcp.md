# Setting up DHCP

Devices on a home LAN are generally allocated IP address automatically when they connect to the network. To do this a DHCP server must be running on the network.

I am assuming you have setup a small LAN with a server, like the one built in this page:

{% content-ref url="setting-up-web-server.md" %}
[setting-up-web-server.md](setting-up-web-server.md)
{% endcontent-ref %}

## Setup DHCP on the Server

1. Click on the _Server_ in your network
2. Click on the _Services_ tab
3. Click on _DHCP_ module
4. Turn DHCP on
5. Set default Gateway to **192.168.0.1** (or the IP of any existing router on this LAN)
6. Set the DNS server to **192.168.0.250** (the IP address of this server)
7. Set the Start of range to **192.168.0.5**
8. Click on _Save_ to save these details as the _serverPool._
9. Close the window

![Server Setup DHCP](<../../.gitbook/assets/image (58).png>)

## Setup IP details on Server

The server itself must have a full manual configuration, otherwise things don't quite work. The server cannot use 'itself' as a DHCP server.

1. Click on the _Server_ to open its config window.
2. Click on _Desktop_ to open the Desktop on the server
3. Click on _IP Configuration_ to open the full IP Configuration application.
4. Setup the full details for IPv4 Address, Subnet Mask, Default Gateway and DNS Server.
5. Close that app on the desktop, then close the window

![Server Desktop](<../../.gitbook/assets/image (57).png>)

![Server Desktop IP configuration](<../../.gitbook/assets/image (56).png>)

## Setup DHCP on each PC

1. Click on PC to open config window
2. Click on _Desktop_ to open module configuration
3. Click on the _IP Configuration_ application
4. Click on _DHCP_ under _IP Configuration_ and it should immediately try and retrieve an IP address and show you what it received.

![PC Desktop](<../../.gitbook/assets/image (59).png>)

![PC IP Configuration](<../../.gitbook/assets/image (60).png>)

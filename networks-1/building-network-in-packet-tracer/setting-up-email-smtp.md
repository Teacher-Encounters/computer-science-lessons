# Setting up Email (SMTP)

This tutorial assumes you have setup a LAN with a server. The server should have DNS enabled.

## Setup Email on Server

1. Click on the server to open it's config window
2. Click on _Services_ to open the module configuration
3. Click on _Email._
4. Enter **marling.school.com** into the _Domain Name_ and click on _Set_.
5. Add a couple of users
   1. User: **bob**, Password: **monkeybusdriver**
   2. User: **alice**, Password: **meltedcremeegg**

![Server Email Configuration](<../../.gitbook/assets/image (64).png>)

![Add Users](<../../.gitbook/assets/image (62).png>)

## Setup DNS for Mail Server

1. Within the _Server_ config window, click on _Services_.
2. Click on the _DNS_ service
3. Add an 'A Record' for **mail.marling.school** that points to the servers IP address.

Note: I had an existing DNS record _mysite.com_ which we could have used, but I'm creating a distinct record just so it looks more like a real life domain.

![Mail Server DNS](<../../.gitbook/assets/image (63).png>)

## Setup Email on PC

1. Click on the PC to bring up the PC Configuration Window
2. Click on _Desktop_ to open the PC desktop
3. Click on _Email_ to bring up the email application
4. Enter the details of one of the users (either bob or alice)
   1. The email address should be bob@marling.school.com, this is a combination of the username and the email domain
5. Repeat on the other PC, but for the other user

![Desktop PC - Select Email](<../../.gitbook/assets/image (66).png>)

![PC Configure Email](<../../.gitbook/assets/image (67).png>)

## Send an Email

Now that each PC is configured with an email address, when you visit the email application you will be presented with a basic email client. You can compose a message from one PC to another.

1. Click on _Compose_.
2. Enter details of email to alice
3. Send the email
4. It should output a log to indicate success
5. Go to the email application on the other PC and check it was received

![PC Email Client](<../../.gitbook/assets/image (68).png>)

![Compose Email](<../../.gitbook/assets/image (69).png>)

![Email Received](<../../.gitbook/assets/image (72).png>)

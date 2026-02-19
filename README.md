*This project has been created as part of the 42 curriculum by karamire*

# Netpractice

---

## DESCRIPTION

Netpractice is a 42 project where we have to configure small-scale networks. To do so, it is necessary to understand how TCP/IP adressing works, including concepts such as subnet mask and default gateway.

____
## INSTRUCTIONS

### Run the training interface

To launch the training interface:

1. Download the .tgz file from the project [page](https://projects.intra.42.fr/projects/netpractice).

2. Unzip the file.

3. Open the index.html file in your web browser.

### Export configuration

When the index.html file is open, you will see 2 differents sections :
- Training
- Evaluation

To start the training exercises, user have to choose the __Training__ one. In this section, you have to enter your intranet
login because moulinette will use it to know your own configuration (see the Submission and Evaluation Part [here](#submission)).
To train for the evaluation, please choose the Evaluation part. Here you have to complete 3 random execises (usually
varying difficulty, e.g., Level 6 to 10) in less than 15 minutes.

### Submission

For each level, a non-functioning network diagram appears. At the top of the window, you will see one or multiple goals to achieve.
Goal: Adjust the available configuration so that the network functions properly.
There are 2 buttons to use:
- CHECK AGAIN : To verify if your configuration is correct or not.
- GET MY CONFIG : To download your configuration whenever you need to. It will be useful to turn in your assignment.

When you completed a level, a new button appears. Click on this button to get to go the next level.

__Important:__ Before moving to the Next Level, you must export your configuration to put it in your Git repository.

Once all levels are finished, just push your Git repository to the intranet so moulinette can use it to evaluate you.

____

## RESSOURCES

### OSI Model

To understand how computer communicate, we use the OSI MODEL. It divide the communication in 7 steps.
Here is 4 of them :
- Layer 1 : Cables, WI-FI, Electrical signal.
- Layer 2 : Data Link, it's where MAC address is (unique identity) and SWITCH too.
- Layer 3 : It's where IP address is managed, and the rooter too.
- Layer 4 : Where the TCP protocol live.

### Switch vs Router

__SWITCH :__
- Role : Connect devices within the same network (like in the room or in the office).
- Example : Connect a computer and a printer together in the same network.
- How it works : Use MAC address to communicate between every devices in the network.

__ROUTER :__
- Role : Link differents networks (like home network and internet).
- How it works : Use IP addresses to direct the data.

### TCP/IP Addressing
It is the universal language of the Internet. For a computer to receive a message, it requires three crucial pieces of information configured on its network card.

#### A. IP Address (The Postal Address)
It is the __unique identifier__ of your machine on the network.

* __IPv4 Format:__ `192.168.1.10`
* It changes if you change networks (just like if you moved houses).

#### B. Subnet Mask
It is the most abstract concept, but the most important for understanding the logic. The mask serves to divide the IP address into two parts: the __Street Name__ (Network) and the __House Number__ (Host).

> __The Neighborhood Analogy:__
> Imagine your IP address is: __3 Rue Jean Jaures__.
> The mask tells the computer: "Everything on 'Rue Jean Jaures' is your local network. You can shout at them directly. Everything else is far away, you must go through the post office."

* __Classic Example:__ `255.255.255.0`
  * This means the first 3 numbers of the IP (`192.168.1`) are the __"Street"__.
  * The last number (`10`) is the __"House"__.
  * If a computer wants to talk to `192.168.1.55`, it knows it is on the __same street__ (thanks to the mask). It goes directly (via the Switch).
  * If it wants to talk to `8.8.8.8` (Google), it sees that it is __not the same street__. It must go out.

#### C. Default Gateway
It is the __exit door__. When your computer realizes (thanks to the mask) that the destination is __not__ on the same "street" (local network), it sends the packet to the gateway.

* Concretely, the gateway is the __IP address of your router__.
* If you do not have a gateway, you can talk to your local printer, but you __cannot__ go on the Internet.

### 4. TCP Protocol (Transmission Control Protocol)
You will often see "TCP/IP". If IP is the address, __TCP__ is the delivery method.

__TCP is reliable.__ Imagine a certified mail with a return receipt.
1.  I send the packet.
2.  You confirm that you received it.
3.  If a piece is missing, I resend it.

It is what we use to load web pages or emails (we do not want missing letters).
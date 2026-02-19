*This project has been created as part of the 42 curriculum by karamire*

# NetPractice

---

## Description

NetPractice is a 42 School project designed to introduce the basics of computer networking. Through 10 progressive levels, the goal is to configure small-scale simulated networks so that they function correctly. Each level presents a broken network diagram, and the task is to fix it by adjusting IP addresses, subnet masks, and routes.

To succeed, it is necessary to understand how **TCP/IP addressing** works, including key concepts such as the **subnet mask**, the **default gateway**, and the role of **routers** and **switches** within a network.

The networks used in this project are **simulated** and are not connected to any real infrastructure.

---

## Instructions

### Running the training interface

1. Download the `.tgz` archive from the project page on the 42 intranet.
2. Extract the files into a folder of your choice.
3. Run the `run.sh` script. It will start a local web server and open the interface in your browser.

### Using the interface

The interface has two tabs:

- **Training** — Enter your 42 intranet login. Moulinette will use it to generate your personal configuration. This is the tab to use when completing levels for submission.
- **Evaluation** — Generates a random configuration. Useful for practicing under exam conditions.

### Completing a level

For each level, a non-functioning network diagram is displayed along with one or more goals to achieve. Modify only the **unshaded fields** until the network is correctly configured.

Two buttons are available:

- **Check again** — Verifies whether your current configuration is correct.
- **Get my config** — Downloads your configuration file for the current level.

Once a level is successfully completed, a **Next level** button appears.

 **Before clicking "Next level", always export your configuration using "Get my config".**

At the bottom of the page, logs are displayed. They explain why a configuration is incorrect (e.g., missing gateway, invalid IP address, unreachable destination). Reading them carefully is essential to debugging your setup.

### Submission

- Complete all **10 levels** using your personal intranet login in the Training tab.
- Export a configuration file for **each level** using the **Get my config** button.
- Place all **10 configuration files** at the **root of your Git repository**.

During the peer-evaluation, you will have to successfully complete **3 random levels** within a limited time. No external tools are allowed, except a basic calculator.

---

## Resources

### Networking concepts studied

This project covers the following core networking concepts:

#### OSI Model

The OSI model divides network communication into 7 layers. The most relevant ones for this project are:

| Layer | Name | Role |
|-------|------|------|
| 1 | Physical | Cables, Wi-Fi, electrical signals |
| 2 | Data Link | MAC addresses, Switches |
| 3 | Network | IP addresses, Routers, routing |
| 4 | Transport | TCP/UDP protocols |

#### Switch vs Router

**Switch** — Operates at Layer 2. Connects devices **within the same network** using MAC addresses. Does not route between different networks.

**Router** — Operates at Layer 3. Connects **different networks** using IP addresses. Reads routing tables to forward packets to their destination.

#### TCP/IP Addressing

For a device to communicate on a network, it needs three things:

**A. IP Address** — A unique identifier for a machine on the network. Format: `192.168.1.10`. An IPv4 address is made of 4 octets (32 bits total).

**B. Subnet Mask** — Splits the IP address into two parts: the **network** portion and the **host** portion. It tells the device which other addresses are on the same local network and which are not.

Example with mask `255.255.255.0` (or `/24` in CIDR notation):
- Network part: `192.168.1` → identifies the network
- Host part: `.10` → identifies the specific device
- All addresses from `192.168.1.1` to `192.168.1.254` are on the same network.
- The address `192.168.1.0` is the **network address** (not assignable).
- The address `192.168.1.255` is the **broadcast address** (not assignable).

**C. Default Gateway** — The IP address of the router interface that a device sends packets to when the destination is **outside** its local network. Without a gateway, communication is limited to the local subnet.

#### CIDR Notation

Subnet masks can be written in two ways:
- Decimal: `255.255.255.0`
- CIDR (prefix): `/24` (meaning 24 bits set to 1)

Common masks:

| CIDR | Mask | Hosts available |
|------|------|-----------------|
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /30 | 255.255.255.252 | 2 |

#### Routing Tables

A router uses a **routing table** to decide where to forward a packet. Each entry has:
- A **destination network** (e.g., `192.168.2.0/24`)
- A **next hop** or **gateway** (where to send the packet next)

The default route `0.0.0.0/0` matches any destination not covered by a more specific rule, and sends the packet to the default gateway.

#### TCP Protocol

TCP (Transmission Control Protocol) is a **reliable**, connection-oriented protocol. It guarantees delivery by requiring acknowledgments and retransmitting lost packets. It is used for web browsing, email, and file transfers where data integrity matters.

#### Reserved IP Ranges (RFC 1918)

These address ranges are reserved for private networks and cannot be routed on the public internet:

| Range | CIDR |
|-------|------|
| 10.0.0.0 – 10.255.255.255 | 10.0.0.0/8 |
| 172.16.0.0 – 172.31.255.255 | 172.16.0.0/12 |
| 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 |

---

### Online References

- **Cisco Networking Basics** — https://www.cisco.com/c/en/us/solutions/small-business/resource-center/networking/networking-basics.html
- **Subnet Mask Cheat Sheet** — https://www.aelius.com/njh/subnet_sheet.html
- **Subnet Calculator** — https://www.subnet-calculator.com/
- **CIDR to Subnet Mask converter** — https://www.ipaddressguide.com/cidr
- **TCP/IP Guide (free online book)** — http://www.tcpipguide.com/free/t_toc.htm
- **ipcalc (online IP calculator)** — https://jodies.de/ipcalc

---

## AI Usage

I used AI assistant at several stages of this project. Here is a transparent description of how and why:

**Understanding difficult concepts** — Some notions like CIDR notation, routing tables, and the difference between network/broadcast addresses were not immediately obvious. I asked Claude to explain them step by step, sometimes with analogies, until I genuinely understood them.

**Generating practice exercises** — To test my comprehension before attempting the levels, I asked Claude to generate small networking exercises (e.g., "given this IP and mask, what is the network address and the valid host range?"). This allowed me to self-evaluate and identify gaps in my knowledge before they became problems during evaluation.

**Structuring this README** — I used Claude to help structure this document in a way that respects the project requirements from the subject PDF.

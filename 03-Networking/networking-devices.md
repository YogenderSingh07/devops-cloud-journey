# How I understood communication inside a computer network

# 🌐 Network Devices

Before learning about IP addresses, subnetting, or routing, I wanted to understand **how two computers actually communicate**. This led me to learn about network devices such as **Hubs, Switches, and Routers**.

Instead of memorizing definitions, I tried to understand **why each device exists** and **what problem it solves**.

---

# Why Do We Need Network Devices?

Imagine connecting ten computers together.

Without a networking device, every computer would need a separate cable to every other computer, creating a huge number of connections that are difficult to manage.

Network devices solve this problem by providing a central point through which devices can communicate.

Different network devices have different responsibilities:

* **Hub** – Simply forwards data to every connected device.
* **Switch** – Sends data only to the intended device within the same network.
* **Router** – Connects different networks together and forwards packets between them.

---

# Hub

A **Hub** is one of the simplest networking devices.

When a device sends data to a hub, the hub **does not inspect the destination**. Instead, it simply copies the incoming data and sends it to **every port**.

```text
          Hub
     ┌────┼────┐
     │    │    │
    PC1  PC2  PC3

PC1 sends data
        │
        ▼
Hub broadcasts it to everyone
```

Even though only one computer is the intended recipient, every connected device receives the data.

The receiving devices check whether the data belongs to them:

* If yes, they process it.
* If not, they discard it.

### Drawbacks of a Hub

* Unnecessary network traffic
* Lower performance
* Higher chance of collisions
* No understanding of connected devices

As networks became larger, hubs became inefficient.

This led to the development of switches.

---

# Switch

A **Switch** is a smarter networking device.

Unlike a hub, a switch **learns which device is connected to each of its ports** by storing their **MAC addresses** in a MAC address table.

Instead of sending data to every computer, it forwards the frame **only to the correct destination**.

```text
         Switch
     ┌────┼────┐
     │    │    │
    PC1  PC2  PC3

PC1 sends data to PC3

Switch forwards it only to PC3.
```

This significantly improves network performance because:

* Less unnecessary traffic
* Better bandwidth utilization
* Fewer collisions
* Faster communication

---

# Why Are Switches Preferred Over Hubs?

The biggest difference is **how they forward data**.

| Hub                             | Switch                                 |
| ------------------------------- | -------------------------------------- |
| Broadcasts data to every device | Sends data only to the intended device |
| Does not know connected devices | Maintains a MAC Address Table          |
| More network congestion         | Efficient communication                |
| Higher collision rate           | Greatly reduces collisions             |
| Lower performance               | Better performance                     |

Because of these advantages, switches have almost completely replaced hubs in modern networks.

---

# If Switches Use MAC Addresses, Why Do We Ping an IP Address?

This was one of the questions that confused me the most.

When we ping another computer, we type its **IP address**, not its MAC address.

For example:

```bash
ping 192.168.1.20
```

But a switch forwards data using **MAC addresses**.

So how does the computer know the destination MAC address?

The answer is **ARP (Address Resolution Protocol)**.

---

# How ARP Works

Suppose my computer wants to ping another computer.

```text
My PC
IP : 192.168.1.10

Destination
IP : 192.168.1.20
```

My computer already knows the destination IP address.

However, the switch needs the **destination MAC address** before it can forward the frame.

The communication happens like this:

### Step 1 — Check the ARP Cache

The operating system first checks whether it already knows the MAC address associated with the destination IP.

If it does, communication begins immediately.

If it doesn't, the computer proceeds to the next step.

---

### Step 2 — Broadcast an ARP Request

The computer sends an ARP Request to every device on the local network.

It is essentially asking:

> "Who has IP address `192.168.1.20`?"

Since this is a broadcast, every device receives it.

---

### Step 3 — The Correct Device Replies

Only the device with that IP address responds.

For example:

```text
192.168.1.20 is at

08:00:27:AA:BB:CC
```

This is called the **ARP Reply**.

---

### Step 4 — Store the Mapping

The sender stores the mapping in its **ARP Cache** so future communication doesn't require another broadcast immediately.

---

### Step 5 — Send the ICMP Packet

Now the computer knows:

* Destination IP Address
* Destination MAC Address

It creates an **ICMP Echo Request** (the packet used by `ping`) and encapsulates it inside an Ethernet frame addressed to the destination MAC.

The switch reads the destination MAC address and forwards the frame only to the correct device.

---

# Communication Flow

```text
PC A
 │
 │ Wants to ping 192.168.1.20
 │
 ▼
Checks ARP Cache
 │
 ├── MAC Found
 │
 └── MAC Not Found
        │
        ▼
Broadcast ARP Request
        │
        ▼
Destination replies with its MAC
        │
        ▼
Create ICMP Echo Request
        │
        ▼
Switch forwards frame using MAC
        │
        ▼
Destination receives packet
        │
        ▼
ICMP Echo Reply
```

This helped me understand why **we communicate using IP addresses**, while **switches still rely on MAC addresses** for delivery within a local network.

---

# Why Isn't a Switch Enough?

After learning about switches, another question came to mind.

If switches are already smart enough to send data only to the correct computer, why do we need routers?

The answer is simple:

A switch only works **inside a single Local Area Network (LAN)**.

Consider these two networks:

```text
Network A
192.168.1.0/24

Network B
10.0.0.0/24
```

A switch in Network A has no knowledge of devices in Network B.

It cannot decide where packets should go outside its own network.

This is where routers become essential.

---

# Router

A **Router** is a Layer 3 networking device that connects **different networks**.

Unlike a switch, a router makes forwarding decisions based on **IP addresses**, not MAC addresses.

You can think of a router as a traffic controller between networks.

```text
Network A
     │
  Switch
     │
  Router
     │
Internet
     │
  Router
     │
  Switch
     │
Network B
```

Without routers, communication would remain limited to devices within the same local network.

---

# How a Router Handles an Incoming Packet

Whenever a router receives a packet, it performs several important steps:

1. Reads the destination IP address.
2. Looks up the destination in its routing table.
3. Determines the best next hop or outgoing interface.
4. Decreases the **TTL (Time To Live)** value by 1 to prevent packets from looping forever.
5. Recalculates the IP header checksum because the header has changed.
6. Encapsulates the packet into a new Layer 2 frame appropriate for the next network.
7. Forwards the packet toward its destination.

Unlike switches, routers do **not** simply forward frames based on MAC addresses. Their job is to move packets between different networks using IP routing.

---

# Key Takeaways

* A **Hub** blindly sends incoming data to every connected device.
* A **Switch** learns MAC addresses and forwards frames only to the intended device within the same LAN.
* **ARP** allows a computer to discover the MAC address associated with a known IP address.
* **ICMP** is the protocol used by the `ping` command to test connectivity.
* A **Router** connects different networks and forwards packets based on IP addresses using its routing table.

Understanding these devices helped me see how data moves from one computer to another—from the local network all the way to other networks and, eventually, across the Internet.



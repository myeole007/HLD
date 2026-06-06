# Day 01 - Interview Revision Notes

# Client vs Server

Client:
Requests service.

Examples:

* Browser
* App

Server:
Processes request and sends response.

---

# DNS

Purpose:

Domain Name → IP Address

Example:

```text
google.com
      ↓
142.xxx.xxx.xxx
```

Analogy:

DNS = Phonebook

---

## DNS Resolution Flow

```text
Browser Cache
    ↓
OS Cache
    ↓
Router Cache
    ↓
DNS Resolver
    ↓
Root DNS
    ↓
TLD DNS (.com)
    ↓
Authoritative DNS
```

---

# IP Address

Purpose:

Find machine/server.

Analogy:

IP = House Address

---

# Port Number

Purpose:

Find service inside machine.

Examples:

```text
80 → HTTP
443 → HTTPS
3306 → MySQL
8080 → API
```

Memory Trick:

> IP finds machine

> Port finds service

---

# TCP 3-Way Handshake

Purpose:

Reliable communication.

Steps:

```text
SYN
↓
SYN + ACK
↓
ACK
```

Memory Trick:

```text
Knock?
↓
Yes?
↓
Coming in.
```

---

# Complete Request Journey

```text
Browser
↓
DNS
↓
IP
↓
Port
↓
TCP Handshake
↓
HTTP Request
↓
Server Response
```

---

# Interview Questions

1. What happens when you type google.com?

2. How DNS works?

3. Why DNS cache needed?

4. Difference between IP and Port?

5. Why TCP handshake needed?

6. Explain TCP 3-way handshake.

---

# Golden Lines

> DNS converts domain → IP

> IP finds machine

> Port finds service

> HLD = Find bottleneck → Solve bottleneck

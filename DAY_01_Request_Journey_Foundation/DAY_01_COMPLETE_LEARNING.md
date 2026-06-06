# Day 01 - Request Journey Foundation

# Goal of Day 1

The goal of Day 1 was to understand:

> How a request reaches a server and how systems communicate over the internet.

Before learning advanced HLD topics like Load Balancer, Cache, Kafka, Database Scaling, etc., it is important to understand:

* How client communicates with server
* How machine is identified
* How service inside machine is identified
* How reliable communication happens

---

# 1. Client and Server

## What is a Client?

A client is an entity that initiates a request for some service.

Examples:

* Browser
* Mobile App
* Desktop Application
* Another Microservice

Example:

When user types:

```text
google.com
```

Browser requests:

> "Give me homepage."

Browser acts as:

> Client

---

## What is a Server?

A server is an entity that processes request and provides response/service.

Example:

Google server responds with:

* HTML
* CSS
* JavaScript

Simple Analogy:

Client = Customer

Server = Restaurant Kitchen

Customer asks for food.

Kitchen prepares and returns food.

---

# 2. DNS (Domain Name System)

## Why DNS Exists?

Humans remember names.

Machines understand numbers (IP addresses).

Without DNS:

Instead of:

```text
google.com
```

Users would need to remember:

```text
142.xxx.xxx.xxx
```

which is impractical.

---

## What DNS Does

DNS converts:

```text
Domain Name → IP Address
```

Example:

```text
google.com
       ↓
142.xxx.xxx.xxx
```

Simple analogy:

DNS works like:

> Phonebook / Contact List

You search:

```text
Rahul
```

Phone finds:

```text
+91xxxxxxxx
```

Similarly:

```text
google.com
```

becomes:

```text
IP Address
```

---

## How DNS Resolution Works

When user types:

```text
google.com
```

system performs lookup.

### Step 1: Browser Cache

Browser checks:

> "Do I already know Google IP?"

If yes:

Done.

---

### Step 2: OS Cache

Operating system checks cache.

If found:

Done.

---

### Step 3: Router Cache

Sometimes router may know.

---

### Step 4: DNS Resolver

Request goes to DNS Resolver.

Usually provided by:

* ISP
* Google DNS (8.8.8.8)
* Cloudflare DNS (1.1.1.1)

Resolver acts like:

> Smart Librarian

---

### Step 5: Recursive Lookup

Resolver asks:

```text
Root DNS
    ↓
.com DNS
    ↓
google.com DNS
    ↓
IP Found
```

Finally browser receives:

```text
142.xxx.xxx.xxx
```

Browser caches result.

---

# 3. IP Address

## Why IP Exists?

Internet needs machine address.

IP identifies:

> Which machine/server should receive request.

Simple analogy:

IP = House Address

Example:

```text
Flat 702
Mumbai
```

Computer equivalent:

```text
142.xxx.xxx.xxx
```

Without IP:

Machine cannot be found.

---

# 4. Port Number

## Why Port Exists?

One machine can run multiple services.

Example:

Same machine may run:

* Website
* API
* Database
* Admin Panel

Question:

How system knows which service to send request?

Answer:

> Port Number

---

## Analogy

IP = Building Address

Port = Flat Number

Example:

```text
Google Machine
142.xxx.xxx.xxx
```

Service:

```text
443 → HTTPS
80 → HTTP
3306 → MySQL
8080 → API
```

Important Memory Line:

> IP finds machine

> Port finds service

---

# 5. TCP Handshake

## Why TCP Exists?

Internet is unreliable.

Packets may:

* get lost
* arrive late
* arrive out of order

TCP provides:

> Reliable communication

Used in:

* REST APIs
* Login systems
* Banking
* Database communication

---

## TCP 3-Way Handshake

Before communication starts:

Connection must be established.

### Step 1 - SYN

Client says:

> "Can we connect?"

---

### Step 2 - SYN + ACK

Server says:

> "Yes, I heard you. Ready to connect."

---

### Step 3 - ACK

Client says:

> "Great, connection confirmed."

Now:

Connection established.

Then actual request begins.

Example:

```text
GET /homepage
```

Simple Analogy:

TCP = Knock before entering room

```text
Knock?
↓
Yes?
↓
Coming in.
```

---

# 6. Complete Request Journey

When user types:

```text
google.com
```

Complete flow:

```text
Browser
    ↓
DNS Lookup
    ↓
IP Address Found
    ↓
Port Selected
    ↓
TCP Handshake
    ↓
HTTP Request Sent
    ↓
Server Processes Request
    ↓
Response Returned
```

---

# 7. Why Single Server Becomes Problem

Single server works initially.

Example:

```text
10 users → fine
100 users → okay
1000 users → slower
100,000 users → problem
```

Possible bottlenecks:

* CPU
* Memory
* Connections
* Network bandwidth
* Database

Key HLD Insight:

> Every system eventually gets bottleneck.

High Level Design is often:

> Find bottleneck → solve bottleneck.

---

# Key Takeaways

1. DNS converts domain → IP

2. IP finds machine

3. Port finds service

4. TCP ensures reliable communication

5. Every system eventually faces bottlenecks

6. HLD is about solving bottlenecks intelligently

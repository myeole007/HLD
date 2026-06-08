# Day 02 - Scaling Foundation

# Goal of Day 2

The goal of Day 2 was to understand:

> Why a single server becomes a bottleneck and how systems scale as traffic grows.

We learned:

* Why one server eventually fails
* Vertical Scaling
* Horizontal Scaling
* Why Load Balancer becomes necessary
* Stateless vs Stateful systems
* URL Shortener V1 thinking

---

# 1. Why Single Server Becomes Problem

Initially:

```text id="d2a1"
Client
   ↓
Server
```

works perfectly.

Example:

```text id="d2a2"
10 users/day
100 users/day
```

No issue.

Problem starts when traffic increases.

Example:

```text id="d2a3"
100,000 users/min
```

One machine has limits.

---

## Important HLD Principle

Every system eventually gets:

> Bottleneck

HLD thinking is:

```text id="d2a4"
Find Bottleneck
       ↓
Solve Bottleneck
```

We should not say:

> System crashed

Instead ask:

> What became bottleneck?

---

## Common Bottlenecks

### 1. CPU Bottleneck

Too much processing.

Example:

```text id="d2a5"
CPU = 100%
```

Result:

Slow response.

---

### 2. Memory (RAM) Bottleneck

Too many requests consume memory.

Example:

```text id="d2a6"
RAM Full
```

Result:

Application slows or crashes.

---

### 3. Network Bottleneck

Bandwidth limit reached.

Example:

Too many users sending requests.

Result:

Slow communication.

---

### 4. Connection Bottleneck

Too many TCP connections.

Example:

```text id="d2a7"
10 users → okay
100k connections → problem
```

---

### 5. Database Bottleneck

Too many reads/writes.

Database becomes slow.

(Deep dive later)

---

# 2. Vertical Scaling (Scale UP)

## What is Vertical Scaling?

Vertical Scaling means:

> Making the same machine stronger.

Example:

Before:

```text id="d2a8"
CPU = 4 Cores
RAM = 8 GB
```

After Upgrade:

```text id="d2a9"
CPU = 32 Cores
RAM = 128 GB
```

Still:

> One machine

---

## Analogy

Restaurant Example:

Instead of opening new restaurants:

We make:

> Bigger kitchen

or

> Super chef

Still one restaurant.

---

## Architecture

Before:

```text id="d2a10"
Clients
   ↓
Server
```

After:

```text id="d2a11"
Clients
   ↓
Bigger Server
(CPU ↑ RAM ↑)
```

---

## Advantages

### Easy to implement

No architecture complexity.

---

### Faster implementation

Upgrade server.

Done.

---

### No Load Balancer needed

Still single machine.

---

## Disadvantages

### 1. Physical limit exists

Cannot infinitely increase CPU/RAM.

---

### 2. Expensive

Powerful machines cost more.

---

### 3. Single Point of Failure

If server crashes:

```text id="d2a12"
System Down
```

---

# 3. Horizontal Scaling (Scale OUT)

## What is Horizontal Scaling?

Horizontal Scaling means:

> Add more servers

instead of making one server stronger.

Example:

Before:

```text id="d2a13"
1 Server
```

After:

```text id="d2a14"
Server 1
Server 2
Server 3
```

---

## Analogy

Restaurant Example:

Instead of:

> Super chef

We hire:

```text id="d2a15"
5 chefs
```

Work distributed.

---

## Architecture

```text id="d2a16"
Clients
   ↓
???
 ↙  ↓  ↘
S1  S2  S3
```

Question appears:

> Who sends request to which server?

Answer:

> Load Balancer

---

## Advantages

### Highly scalable

Can add:

```text id="d2a17"
5 → 10 → 100 servers
```

---

### Fault tolerance

If one server crashes:

Others still work.

---

### Better for large systems

Used by:

* Google
* Netflix
* Amazon

---

## Disadvantages

### More complexity

Now system coordination needed.

Questions arise:

* Which server handles request?
* How state shared?
* How failures handled?

---

# 4. Why Load Balancer Exists

Problem:

Multiple servers exist.

Question:

> Which server should receive request?

Example:

```text id="d2a18"
S1
S2
S3
```

Need traffic manager.

Solution:

> Load Balancer

---

## Basic Idea

```text id="d2a19"
          LB
        /  |  \
      S1  S2  S3
```

Load Balancer distributes traffic.

Analogy:

> Traffic Police

(No deep dive yet)

---

# 5. Stateless vs Stateful

## Stateful

Meaning:

> Server remembers user information.

Example:

```text id="d2a20"
Login State
Shopping Cart
Session
```

Problem:

If next request goes to different server:

```text id="d2a21"
User → Server 2
```

Server 2 does not know state.

---

## Stateless

Meaning:

> Server remembers nothing.

Every request contains everything needed.

Example:

```text id="d2a22"
Token
User Data
Request Data
```

Any server can process request.

---

## Important Principle

```text id="d2a23"
Stateful → Server remembers

Stateless → Request remembers
```

---

## Why Stateless Preferred?

Because:

> Easier Horizontal Scaling

Request can go:

```text id="d2a24"
S1
S2
S3
```

No issue.

---

# 6. URL Shortener V1

For first version:

Simple architecture preferred.

```text id="d2a25"
Client
   ↓
Single Server
   ↓
Database
```

Why?

Traffic low.

No need to overengineer.

---

## APIs Needed

### Create Short URL

Input:

Long URL

Output:

Short URL

---

### Redirect URL

Input:

Short URL

Output:

Original URL

---

## Important HLD Principle

> Build for current scale

> Design for future scale

Do not overengineer.

---

# Key Takeaways

1. Every system eventually gets bottleneck

2. Vertical Scaling = Scale UP

3. Horizontal Scaling = Scale OUT

4. Load Balancer introduced because of multiple servers

5. Stateless scales easier than Stateful

6. Start simple and evolve system gradually

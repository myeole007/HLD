# Day 02 - Interview Revision Notes

# Single Server Bottleneck

Resources are limited:

* CPU
* RAM
* Network
* Connections
* Database

Golden Line:

> Find bottleneck → Solve bottleneck

---

# Vertical Scaling

Meaning:

> Scale UP

Make machine stronger.

Example:

```text id="d2r1"
CPU ↑
RAM ↑
```

Pros:

* simple
* easy

Cons:

* expensive
* limit exists
* single point of failure

---

# Horizontal Scaling

Meaning:

> Scale OUT

Add more servers.

Example:

```text id="d2r2"
S1
S2
S3
```

Pros:

* scalable
* fault tolerant

Cons:

* more complexity

---

# Why Load Balancer?

Multiple servers problem:

> Who handles request?

Solution:

```text id="d2r3"
          LB
        /  |  \
      S1  S2  S3
```

Analogy:

Traffic Police.

---

# Stateful vs Stateless

Stateful:

> Server remembers

Problem:

Scaling difficult.

---

Stateless:

> Request remembers

Better for scaling.

Golden Line:

> Stateless scales easier horizontally

---

# URL Shortener V1

Architecture:

```text id="d2r4"
Client
   ↓
Server
   ↓
DB
```

Why?

Less users.

Avoid overengineering.

---

# Interview Questions

1. Why single server becomes bottleneck?

2. Vertical vs Horizontal scaling?

3. Pros/cons of Vertical Scaling?

4. Why Load Balancer needed?

5. Stateful vs Stateless?

6. Why Stateless scales better?

7. Design URL Shortener V1?

---

# Golden Lines

> Scale UP = Bigger machine

> Scale OUT = More machines

> Stateless scales easier

> Build for current scale, design for future scale

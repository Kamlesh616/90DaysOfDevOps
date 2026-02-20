# 🌐 Day 14 – Networking Fundamentals & Hands-on Checks

## 🎯 Objective
Understand core networking concepts and practice essential troubleshooting commands in Linux.

---

# 📚 Quick Concepts

## 🔹 OSI Model (L1–L7)

1. **Physical (L1)** – Cables, signals, hardware.
2. **Data Link (L2)** – MAC address, switching.
3. **Network (L3)** – IP addressing & routing.
4. **Transport (L4)** – TCP / UDP communication.
5. **Session (L5)** – Session management.
6. **Presentation (L6)** – Encryption, formatting.
7. **Application (L7)** – HTTP, DNS, FTP, SSH.

---

## 🔹 TCP/IP Model

1. **Link** – Physical + Data Link  
2. **Internet** – IP routing  
3. **Transport** – TCP / UDP  
4. **Application** – HTTP, HTTPS, DNS, SSH  

---

## 🔹 Where Protocols Sit

- **IP** → Internet Layer  
- **TCP/UDP** → Transport Layer  
- **HTTP/HTTPS** → Application Layer  
- **DNS** → Application Layer  

---

## 🔹 Real Example

`curl https://example.com`  

Application (HTTP) → Transport (TCP) → Internet (IP) → Link  

---

# 🏏 OSI Model Example – Virat Sends a Message to Anushka

Imagine **Virat Kohli** sends a WhatsApp message to **Anushka Sharma**:

💬 _"Dinner at 8 PM ❤️"_

Let’s see how this message travels through the OSI layers.

---

## 7️⃣ Application Layer (L7)

- Virat types the message in WhatsApp.
- App prepares data to send.

---

## 6️⃣ Presentation Layer (L6)

- Message converted into binary.
- Encrypted for security.

---

## 5️⃣ Session Layer (L5)

- WhatsApp checks if Anushka is online.
- Session between devices is established.

---

## 4️⃣ Transport Layer (L4)

- TCP ensures reliable delivery.
- Data is broken into segments.
- Ensures correct order & retransmission if lost.

---

## 3️⃣ Network Layer (L3)

- Source IP → Virat’s phone IP  
- Destination IP → Anushka’s phone IP  
- Routing happens across the internet.

---

## 2️⃣ Data Link Layer (L2)

- Frames created.
- MAC addresses used inside local network.

---

## 1️⃣ Physical Layer (L1)

- Data travels as:
  - WiFi signals  
  - Mobile data  
  - Fiber optic cables  

---

## 📥 On Anushka’s Side

The process reverses:

Physical → Data Link → Network → Transport → Session → Presentation → Application  

Finally, she reads:

💬 _"Dinner at 8 PM ❤️"_

---

# 🧪 Hands-on Checklist  
**Target Used:** `google.com`

---

## ✅ 1. Identity Check

```bash
hostname -I
```

**Observation:** Shows system IP address.

---

## ✅ 2. Reachability Test

```bash
ping google.com
```

**Observation:**  
- Latency around 20–30 ms  
- 0% packet loss  
- Host reachable  

---

## ✅ 3. Path Check

```bash
traceroute google.com
```

**Observation:**  
- Multiple hops  
- No major delay or timeout  

---

## ✅ 4. Check Listening Ports

```bash
ss -tulpn
```

**Observation:**  
- SSH running on port 22  
- Nginx running on port 80  

---

## ✅ 5. Name Resolution

```bash
dig google.com
```

**Observation:**  
- Domain resolves to public IP  

---

## ✅ 6. HTTP Check

```bash
curl -I https://google.com
```

**Observation:**  
- HTTP status code **200 OK**  
- Service reachable  

---

## ✅ 7. Connections Snapshot

```bash
netstat -an | head
```

**Observation:**  
- Some ESTABLISHED connections  
- Some LISTEN services  

---

# 🔎 Mini Task – Port Probe & Interpret

### Identified Listening Port:
SSH → Port 22

```bash
nc -zv localhost 22
```

**Result:** Connection succeeded.

If not reachable → Next checks:
- `systemctl status ssh`
- Check firewall (`ufw status`)

---

# 🧠 Reflection

### 🔹 Fastest Signal When Something Breaks?
`ping` gives fastest connectivity check.

---

### 🔹 If DNS Fails?
Check Application Layer (DNS) and `/etc/resolv.conf`.

---

### 🔹 If HTTP 500 Appears?
Inspect:
- Web server logs  
- Backend service  
- Database connectivity  

---

### 🔹 Two Real Incident Follow-up Checks

1. `systemctl status nginx`
2. Check logs in `/var/log/nginx/`

---

# 🚀 What I Learned

- How OSI and TCP/IP models map to real-world networking.
- How data flows layer by layer.
- Basic Linux networking troubleshooting steps.
- How to verify if a service is reachable.

---

✅ Completed Networking Fundamentals & Hands-on Checks

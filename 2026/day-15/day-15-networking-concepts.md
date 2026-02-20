# 🌐 Day 15 – Networking Concepts: DNS, IP, Subnets & Ports

## 🎯 Objective
Understand the core networking building blocks every DevOps engineer must know: DNS, IP addressing, CIDR/subnetting, and ports.

---

# 🧩 Task 1 – DNS: How Names Become IPs

## 🔹 What Happens When You Type `google.com`?

1. Browser checks local cache for the IP.
2. If not found, it asks the DNS resolver.
3. Resolver queries DNS servers (Root → TLD → Authoritative).
4. DNS returns the IP address, and browser connects to that IP.

---

## 🔹 DNS Record Types

- **A** – Maps domain to IPv4 address.
- **AAAA** – Maps domain to IPv6 address.
- **CNAME** – Alias of one domain to another.
- **MX** – Mail server for the domain.
- **NS** – Nameserver responsible for the domain.

---

## 🔹 Command: Check A Record

```bash
dig google.com
```

### Sample Output (Important Section)

```bash
google.com.     300   IN   A   142.250.183.14
```

- **A Record:** 142.250.183.14  
- **TTL:** 300 seconds  

---

# 🌍 Task 2 – IP Addressing

## 🔹 What is an IPv4 Address?

An IPv4 address is a 32-bit number written in dotted decimal format.

Example: `192.168.1.10`

Structure:
- 4 octets
- Each octet ranges from 0–255

---

## 🔹 Public vs Private IP

- **Public IP** – Accessible over the internet  
  Example: `8.8.8.8`

- **Private IP** – Used inside local networks  
  Example: `192.168.1.10`

---

## 🔹 Private IP Ranges

- `10.0.0.0 – 10.255.255.255`
- `172.16.0.0 – 172.31.255.255`
- `192.168.0.0 – 192.168.255.255`

---

## 🔹 Command: Identify Private IP

```bash
ip addr show
```

### Sample Output

```bash
inet 192.168.1.10/24 brd 192.168.1.255 scope global dynamic
```

- `192.168.1.10` → Private IP

---

# 🧮 Task 3 – CIDR & Subnetting

## 🔹 What Does `/24` Mean?

`192.168.1.0/24` means:
- 24 bits are network bits.
- 8 bits are host bits.
- Subnet mask = `255.255.255.0`

---

## 🔹 Usable Hosts Calculation

| CIDR | Total IPs | Usable Hosts |
|------|-----------|--------------|
| /24  | 256       | 254          |
| /16  | 65,536    | 65,534       |
| /28  | 16        | 14           |

Formula:
```
Total IPs = 2^(32 - CIDR)
Usable = Total - 2
```

---

## 🔹 Why Do We Subnet?

- To divide large networks into smaller parts.
- Improve security and organization.
- Reduce broadcast traffic.
- Better IP management.

---

## 🔹 Quick Exercise

| CIDR | Subnet Mask       | Total IPs | Usable Hosts |
|------|-------------------|-----------|--------------|
| /24  | 255.255.255.0     | 256       | 254          |
| /16  | 255.255.0.0       | 65,536    | 65,534       |
| /28  | 255.255.255.240   | 16        | 14           |

---

# 🚪 Task 4 – Ports: The Doors to Services

## 🔹 What is a Port?

A port is a logical communication endpoint.

We need ports because:
- One server can run multiple services.
- Ports identify which service should handle traffic.

---

## 🔹 Common Ports

| Port  | Service        |
|--------|---------------|
| 22     | SSH           |
| 80     | HTTP          |
| 443    | HTTPS         |
| 53     | DNS           |
| 3306   | MySQL         |
| 6379   | Redis         |
| 27017  | MongoDB       |

---

## 🔹 Check Listening Ports

```bash
ss -tulpn
```

### Sample Output

```bash
tcp   LISTEN  0  128  0.0.0.0:22   users:(("sshd",pid=1023))
tcp   LISTEN  0  128  0.0.0.0:80   users:(("nginx",pid=2045))
```

- Port 22 → SSH  
- Port 80 → HTTP (Nginx)

---

# 🔗 Task 5 – Putting It Together

## 🔹 Scenario 1

`curl http://myapp.com:8080`

Involved concepts:
- DNS resolves `myapp.com` to IP.
- TCP connection to port 8080.
- HTTP request sent over TCP.
- IP routing delivers packets.

---

## 🔹 Scenario 2

App can't reach database at `10.0.1.50:3306`

First checks:
- Is MySQL running on port 3306?
- Is port 3306 open (firewall/security group)?
- Can we ping 10.0.1.50?
- Is subnet routing correct?

---

# 🚀 What I Learned

- How DNS converts domain names into IP addresses.
- Difference between public and private IPs.
- CIDR and subnetting basics.
- Importance of ports in service communication.
- How all concepts connect in real-world DevOps troubleshooting.

---

✅ Completed Day 15 – Networking Concepts

---

# 🔥 Firewall in Linux (firewalld)

A **Firewall** is a network security system that monitors and controls **incoming and outgoing network traffic** based on predefined security rules.

In Linux systems (especially **RHEL / CentOS / Rocky Linux**), the firewall is commonly managed using **`firewalld`**.

This guide explains basic **firewalld commands and zones** used in Linux administration. 

---

# 🚀 Starting and Enabling Firewall

Start the firewall service:

```bash
sudo systemctl start firewalld
```

Enable firewall at system boot:

```bash
sudo systemctl enable firewalld
```

Check firewall status:

```bash
sudo firewall-cmd --state
```

Reload firewall rules after making changes:

```bash
sudo firewall-cmd --reload
```

---

# 📋 Checking Firewall Zones

List all available zones:

```bash
sudo firewall-cmd --get-zones
```

Check active zones:

```bash
sudo firewall-cmd --get-active-zones
```

List all rules in the **public** zone:

```bash
sudo firewall-cmd --zone=public --list-all
```

---

# 🌐 Allowing Services

Allow **HTTP temporarily**:

```bash
sudo firewall-cmd --zone=public --add-service=http
```

Allow **HTTP permanently**:

```bash
sudo firewall-cmd --zone=public --add-service=http --permanent
```

---

# ❌ Removing Services

Remove **SSH access** from the public zone permanently:

```bash
sudo firewall-cmd --zone=public --remove-service=ssh --permanent
```

Reload firewall after making permanent changes:

```bash
sudo firewall-cmd --reload
```

---

# 🔌 Opening Custom Ports

Open **port 8080 for TCP traffic**:

```bash
sudo firewall-cmd --zone=public --add-port=8080/tcp --permanent
```

Reload firewall:

```bash
sudo firewall-cmd --reload
```

---

# 🚫 Blocking Traffic from a Specific IP

Block traffic from IP **192.168.1.100**:

```bash
sudo firewall-cmd --add-rich-rule='rule family="ipv4" source address="192.168.1.100" reject' --permanent
```

Reload firewall:

```bash
sudo firewall-cmd --reload
```

---

# 🛡️ Firewalld Zones

Firewalld uses **zones** to define the level of trust for network connections.

### drop

All incoming packets are dropped without any response.

### block

Incoming connections are rejected with an ICMP message.

### public

Used in public areas. Only selected incoming connections are allowed.

### external

Used for external networks with **masquerading enabled** (commonly routers).

### dmz

Used for systems that are publicly accessible but isolated from internal networks.

### work

Used in work environments where most systems are trusted.

### home

Used in home networks where systems are mostly trusted.

### internal

Used for internal networks with trusted devices.

### trusted

All network connections are accepted.

---

# 📚 Useful for

* RHCSA / RHCE preparation
* Linux system administration
* Network security configuration
* Managing firewall rules in production servers

---

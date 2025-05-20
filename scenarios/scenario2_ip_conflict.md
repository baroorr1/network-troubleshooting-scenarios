# Scenario 2: IP Address Conflict

### 📝 Problem
A user reports they have suddenly lost internet connectivity and sees a warning about a duplicate IP address on the network.

### 🔍 Diagnosis Steps & Output

```bash
ipconfig
```
**Result:** Shows an IP address but network is limited or disconnected.

![IPConfig Conflict](https://github.com/baroorr1/network-troubleshooting-scenarios/raw/main/images/conflict.png)

```bash
arp -a
```
**Result:** Displays multiple entries with the same IP address.

![ARP Conflict](https://github.com/baroorr1/network-troubleshooting-scenarios/raw/main/images/arp_conflict.png)

**Windows Notification or Event Viewer:**
Duplicate IP warning may appear as a pop-up or log.

![Conflict Warning](https://github.com/baroorr1/network-troubleshooting-scenarios/raw/main/images/ip_conflict_warning.png)

### 🧠 Root Cause
Another device on the network was manually assigned the same static IP, creating a conflict.

### 🔧 Resolution

**Option 1: Switch to DHCP**
```bash
netsh interface ip set address "Wi-Fi" dhcp
ipconfig /release
ipconfig /renew
```

**Option 2: Use a different static IP**
```bash
netsh interface ip set address "Wi-Fi" static 192.168.1.55 255.255.255.0 192.168.1.1
```

**Verify the fix:**
```bash
ipconfig
ping 8.8.8.8
```

![Resolved IPConfig](https://github.com/baroorr1/network-troubleshooting-scenarios/raw/main/images/last.png)

### 🛡️ Prevention Tips
- Avoid manually assigning static IPs on networks that use DHCP
- Use DHCP reservations via router if static IPs are required
- Monitor your network with tools that detect IP conflicts

**Tags:** `#IPConflict`, `#Networking`, `#Troubleshooting`, `#HelpDesk`, `#Windows`

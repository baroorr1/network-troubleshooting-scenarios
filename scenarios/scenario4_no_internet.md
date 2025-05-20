# Scenario 4: No Internet Access

### 📝 Problem
The user reports that their computer is connected to Wi-Fi, but there is no internet access. No websites load in the browser, and the network icon may show a warning symbol or “No Internet.”

---

### 🔍 Diagnosis Steps & Output

```bash
ipconfig
```
**Result:** Device has a valid IP and default gateway, or it may show an APIPA address (`169.254.x.x`) which means it didn't get an IP from the router.

```bash
ping 192.168.1.1
```
**Result:** Ping to the router is successful — confirms local connectivity. If it fails, issue is between the device and router.

```bash
ping 8.8.8.8
```
**Result:** Fails — confirms there's no access to the internet (not a DNS problem).

```bash
ping google.com
```
**Result:** Fails — DNS resolution not working or there's no connectivity.

```bash
nslookup google.com
```
**Result:** Times out or shows “DNS server not responding.”

---

### 🧠 Root Cause
- The router may have lost internet connection
- DNS server not responding
- DHCP not assigning valid IP
- Firewall or VPN blocking connectivity

---

### 🔧 Resolution Steps

#### 1. Renew the IP address
```bash
ipconfig /release
ipconfig /renew
```

#### 2. Set a public DNS server manually
```bash
netsh interface ip set dns "Wi-Fi" static 8.8.8.8
ipconfig /flushdns
```

#### 3. Reset the network stack
```bash
netsh int ip reset
netsh winsock reset
```

#### 4. Reboot the system

---

### 🔁 Confirmation

```bash
ping google.com
```
**Result:** Internet access restored; successful replies confirm resolution.

---

### 🛡️ Prevention Tips

- Ensure router is online and connected to ISP
- Use automatic IP and DNS assignment (DHCP)
- Keep network adapter drivers updated
- Reboot router and PC if issue recurs
- Temporarily disable firewall/VPN if they are suspected

**Tags:** `#NoInternet`, `#DNSIssue`, `#Connectivity`, `#Troubleshooting`, `#HelpDesk`

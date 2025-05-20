# Scenario 3: Slow Network Response

### 📝 Problem
A user reports that their internet connection is very slow. Websites take a long time to load, downloads are sluggish, and video calls experience lag.

---

### 🔍 Diagnosis Steps & Output

```bash
ping google.com
```
**Result:** Latency ranged from 8ms to 18ms with 0% packet loss, indicating no visible issue under normal load.

```bash
ping 192.168.1.1
```
**Result:** Gateway responded with stable low latency, confirming the local connection to the router is stable.

```bash
tracert google.com
```
**Result:** Traceroute completed successfully. All hops responded within expected time ranges.

```bash
netstat -o
```
**Result:** No unusual or unexpected open connections observed. Network usage appears normal.

---

### 🧠 Root Cause
There was no actual slowdown observed during testing. However, users may report this issue due to:
- Temporary congestion
- High background bandwidth usage
- Interference on Wi-Fi network
- DNS resolution delays

---

### 🔧 Resolution Steps

Executed the following network reset commands to proactively refresh all network settings:

```bash
ipconfig /flushdns
netsh int ip reset
netsh winsock reset
```

System rebooted after the commands to apply changes.

---

### 🔁 Confirmation

```bash
ping google.com
```
**Result:** Re-tested ping showed consistent latency (~11ms average), confirming that the connection remains healthy post-reset.

---

### 🛡️ Prevention Tips

- Reboot router periodically
- Keep network drivers and router firmware up to date
- Use a wired connection for latency-sensitive tasks
- Limit unnecessary background bandwidth usage
- Consider changing Wi-Fi channel to avoid interference

**Tags:** `#SlowNetwork`, `#Latency`, `#Diagnostics`, `#WiFi`, `#HelpDesk`

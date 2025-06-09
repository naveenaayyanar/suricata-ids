````markdown
# 🛡️ Suricata IDS Project Report

## 🎯 Objective

The goal of this project was to install, configure, and operate **Suricata**, an open-source **Network Intrusion Detection System (NIDS)**, on **Kali Linux** to monitor and respond to suspicious network activity.

---

## 🛠️ Tools & Technologies

- **OS**: Kali Linux
- **IDS**: Suricata 7.0.10
- **Firewall**: iptables
- **Logging**: fast.log and eve.json

---

## 🔧 Step-by-Step Implementation

### 1. Install Suricata
```bash
sudo apt update
sudo apt install suricata
````

Installed Suricata from official repositories using APT.

---

### 2. Enable and Start Suricata

```bash
sudo systemctl enable suricata
sudo systemctl start suricata
sudo systemctl status suricata
```

* Enabled Suricata as a system service to run on boot.
* Confirmed it started successfully and is actively monitoring traffic.

---

### 3. View Network Alerts

```bash
sudo cat /var/log/suricata/fast.log
```

Suricata detected suspicious behavior including:

* TCP retransmissions
* DHCP request containing "Kali" in hostname

Sample output:

```
06/09/2025-09:15:41.582408  [**] [1:2022973:1] ET INFO Possible Kali Linux hostname in DHCP Request Packet [**]
```

---

### 4. Block Malicious IP

Based on alerts, malicious IPs were blocked:

```bash
sudo iptables -A INPUT -s 116.119.212.207 -j DROP
```

Blocked an IP with excessive suspicious traffic.

---

### 5. Verify or Delete `iptables` Rules

```bash
sudo iptables -L -n --line-numbers
sudo iptables -D INPUT <line_number>   # (if needed)
```

---

### 6. (Optional) Make Firewall Rules Persistent

```bash
sudo apt install iptables-persistent
sudo netfilter-persistent save
```

To ensure firewall rules remain after reboot.

---

## 📂 Project Files Structure

```
suricata-project/
├── README.md          # Project overview and instructions
├── report.md          # This project report
├── commands.txt       # All terminal commands with explanations
├── screenshots/       # Output screenshots (status, logs, etc.)
```

---

## 📌 Observations

* Suricata worked effectively out-of-the-box with its default ruleset.
* Alerts were meaningful and helped identify potential threats.
* Manual IP blocking added an extra layer of response.
* `fast.log` was easy to parse, and `eve.json` can be used for advanced analysis.

---

## ✅ Conclusion

The project was successfully completed. Suricata was deployed on Kali Linux, used to monitor network traffic, detect anomalies, and respond to them using firewall controls.

---

 -👨‍💻 by

**\{naveena}**

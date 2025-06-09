🔐 Suricata IDS Project

This project demonstrates how to install, configure, and run Suricata, a powerful Network Intrusion Detection System (NIDS), on Kali Linux. The goal was to monitor network traffic, detect suspicious behavior, and optionally respond to detected threats.


📋 Tasks Completed

✅ 1. Installed and ran Suricata as a system service
- Used `apt` to install Suricata
- Enabled it to run at system startup
- Verified active monitoring via `systemctl`

✅ 2. Configured default rules
- Used Suricata's built-in rule sets
- Observed alerts in `fast.log` and optionally in `eve.json`

✅ 3. Detected network-based threats
- Captured alerts like:
  - Excessive TCP retransmissions
  - Kali hostname exposure in DHCP request

✅ 4. Responded to threats manually
- Used `iptables` to block a malicious IP:
  ```bash
  sudo iptables -A INPUT -s 116.119.212.207 -j DROP
  ✅ 5. Verified logs

Accessed alerts with:
 ```bash
sudo cat /var/log/suricata/fast.log


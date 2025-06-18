# 🔍 Analysis – Wireshark Network Traffic Analysis

This document summarizes the network activity captured during the Nmap scan and highlights the key observations and lessons learned.

---

## 📊 Observations

- The Kali Linux machine (192.168.56.101) initiated a scan against the Windows VM (192.168.56.102).
- Wireshark captured a series of **SYN packets** indicating a **stealth scan** using Nmap.
- The packets had the SYN flag set but no ACK response (indicating half-open connections).
- Display filters like `tcp.flags.syn == 1 && tcp.flags.ack == 0` effectively isolated the Nmap activity.
- The source and destination IPs confirmed attacker-victim traffic flow.

---

## 💡 What I Learned

- How to build an isolated virtual lab using VirtualBox
- How to configure host-only networks for direct VM-to-VM communication
- How Nmap scans work and what packet patterns they produce
- How to use Wireshark to analyze and filter packet data
- How attackers can be detected through careful packet inspection

---

## ✅ Conclusion

This project gave me hands-on experience with both Red Team (attacker) and Blue Team (defender) perspectives. I now understand how reconnaissance traffic looks on the network and how to detect it using Wireshark.

It also helped me improve documentation and organization skills — making the project GitHub-ready with setup steps, logs, screenshots, and learnings.

# 🛠️ Project Setup – Wireshark Network Traffic Analysis

This document details how the virtual lab was created, how each component was configured, and how the network traffic was captured for analysis.

---

## ✅ Step 1: Create Project Folder Structure

- Created a new folder named `wireshark-traffic-analysis`
- Inside the folder, the following files and subfolder were created:

wireshark-traffic-analysis/
├── README.md  
├── setup.md  
├── analysis.md  
└── screenshots/

[Project folder structure](screenshots/01_project_folder_structure.png)

---

## ✅ Step 2: VirtualBox Lab Setup

- Started two virtual machines:
  - Kali Linux (Attacker): `192.168.56.101`
  - Windows 10 (Victim): `192.168.56.102`
- Both VMs were configured with Host-Only Network Adapter
- Verified IP addresses:
  - Kali: `ip a`
  - Windows: `ipconfig`

[VirtualBox vms network setup](screenshots/02_virtualbox_vms_network_setup.png)

---

## ✅ Step 3: Start Wireshark on Windows VM

- Launched Wireshark inside the Windows VM
- Selected the correct Host-Only Ethernet Adapter
- Started live packet capture

[Wireshark capture started](screenshots/03_wireshark_capture_started.png)

---

## ✅ Step 4: Simulate Nmap Attack from Kali

- On Kali Linux, opened the terminal and ran the following command:

nmap -sS -A 192.168.56.102

- `-sS` = Stealth SYN scan  
- `-A` = OS detection, version detection, script scan, traceroute

[Kali nmap scan running](screenshots/04_kali_nmap_scan_running.png)

---

## ✅ Step 5: Analyze Captured Traffic in Wireshark

- Returned to Wireshark (on Windows) while Nmap was running
- Applied filters:

ip.addr == 192.168.56.101  
tcp.flags.syn == 1 && tcp.flags.ack == 0

- Observed SYN packets from the Kali IP to Windows IP
- Verified attacker activity

[Wireshark detects nmap scan](screenshots/05_wireshark_detects_nmap_scan.png)

---

This setup provides a safe and realistic simulation of a network being scanned by an attacker. It’s useful for both learning and demonstrating defensive monitoring skills.

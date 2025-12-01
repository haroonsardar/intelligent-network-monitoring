# Intelligent Network Monitoring and Traffic Analysis System

## 🚀 Project Overview
This project demonstrates the implementation of a secure and monitored Local Area Network (LAN) environment using Cisco Packet Tracer. The core focus is on enhancing network security through rule-based access control and enabling real-time traffic anomaly detection.

**Keywords:** Cisco Packet Tracer, Network Security, ACL, Wireshark, Traffic Monitoring, Ping Flood Detection.

---

## ✨ Key Features
* **Network Segmentation:** Server is isolated on a dedicated interface for better control.
* **Rule-Based Security:** Implementation of Access Control Lists (ACLs) to filter traffic.
* **Unauthorized Access Prevention:** Explicitly blocks 'Guest' user (PC1) from accessing the Server.
* **Traffic Anomaly Detection:** Demonstrates the use of Wireshark to identify abnormal traffic patterns (e.g., Ping Flood).

---

## 🛠️ Tools & Technologies Used
* **Cisco Packet Tracer:** Used for designing, simulating, and configuring the network topology.
* **Router:** Cisco 2911 (or 4331)
* **Switch:** Cisco 2960
* **Wireshark:** Used for live packet capture and analysis.

---

## 💻 Setup & Configuration Guide

To replicate this project, follow the configuration steps detailed in the provided `CONFIGURATION_GUIDE.txt` file.

### **1. IP Addressing Scheme**

| Device | Interface | IP Address | Role |
| :--- | :--- | :--- | :--- |
| **Router (R1)** | Gi0/0 | `192.168.1.1` | Gateway for PCs |
| **Router (R1)** | Gi0/1 | `192.168.2.1` | Gateway for Server |
| **PC0** | N/A | `192.168.1.2` | Admin/Allowed User |
| **PC1** | N/A | `192.168.1.3` | **Guest/Blocked User** |
| **Server0** | N/A | `192.168.2.10` | Target Server |

### **2. Security Rule Applied (ACL 100)**

The following rule is configured on **Router Gi0/0 (Inbound)**:
1.  `access-list 100 deny ip host 192.168.1.3 host 192.168.2.10`
    * *(Action: Blocks PC1 from reaching the Server.)*
2.  `access-list 100 permit ip any any`
    * *(Action: Allows all other legitimate traffic.)*

---

## ✅ Verification Steps

1.  **ACL Verification:**
    * Attempt `ping 192.168.2.10` from **PC1** (Guest). **Result MUST be "Destination host unreachable"**.
2.  **Traffic Monitoring:**
    * Run `ping [Server IP] -t` from PC0 (or any external source).
    * Launch **Wireshark** and apply the filter `icmp`. Verify that a flood of Echo Request packets is captured.

---

## 📁 Repository Files

* `Network_Monitoring_Topology.pkt`: The Cisco Packet Tracer project file.
* `CONFIGURATION_GUIDE.txt`: Step-by-step commands and setup guide.
* `README.md`: This description file.

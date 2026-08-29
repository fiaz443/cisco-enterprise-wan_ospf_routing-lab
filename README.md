# Multi-Site Enterprise WAN Routing with OSPF (Single-Area)

## 📌 Project Overview
This project simulates a multi-site enterprise Wide Area Network (WAN) interconnecting three branch offices: **Lahore (R-LHR)**, **Karachi (R-KHI)**, and **Islamabad (R-ISB)**. The core objective is to configure **Open Shortest Path First (OSPF Area 0)** dynamic routing over Serial Point-to-Point WAN links to achieve full end-to-end IP convergence, optimal path selection, and automatic fault-tolerant rerouting across remote branch LANs.

---

## 🛠️ Network Components & Topology Specs
* **WAN Routing Tier:** 3x Cisco 2811 Integrated Services Routers (`R-LHR`, `R-KHI`, `R-ISB`)
* **LAN Switching Tier:** 3x Cisco Catalyst 2950-24 FastEthernet Switches
* **WAN Physical Layer:** Serial DCE/DTE Point-to-Point Serial Cables
* **End Stations:** Branch Host PCs across all three regions
* **Routing Protocol:** OSPFv2 (Open Shortest Path First - Single Area 0)
* **Simulation Tool:** Cisco Packet Tracer

---

## 🗺️ Network Topology Diagram
![Topology Diagram](https://raw.githubusercontent.com/fiaz443/cisco-enterprise-wan_ospf_routing-lab/main/AESD.jpeg)

## ⚙️ Key Configuration Implementation

### 1. WAN Serial Interface & Clock Rate Setup (e.g., R-LHR DCE)
```cisco
Router-LHR(config)# interface Serial0/3/0
Router-LHR(config-if)# ip address 10.0.0.1 255.255.255.252
Router-LHR(config-if)# clock rate 64000
Router-LHR(config-if)# no shutdown

OSPF OSPF-Dynamic-Routing 
Router-LHR(config)# router ospf 1
Router-LHR(config-router)# router-id 1.1.1.1
Router-LHR(config-router)# network 10.0.0.0 0.0.0.3 area 0
Router-LHR(config-router)# network 10.0.0.4 0.0.0.3 area 0
Router-LHR(config-router)# network 192.168.10.0 0.0.0.255 area 0
Router-LHR(config-router)# passive-interface FastEthernet0/0


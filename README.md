# Advance_NSG_Lab

## 📌 Project Overview

This project demonstrates the implementation of advanced network security configurations using Azure Network Security Group in Microsoft Azure.

The lab focuses on controlling inbound and outbound traffic between Virtual Machines using NSG rules, priorities, and real-world troubleshooting scenarios.

## 🧱 Architecture
VNet (10.0.0.0/16)
│
├── Subnet-1 (VM1)
│     └── NSG attached
│
├── Subnet-2 (VM2)
      └── NSG attached
Two Virtual Machines deployed in separate subnets
NSG applied at subnet/NIC level
Traffic controlled using custom rules
## 🎯 Objectives
Understand NSG rule processing (priority-based)
Allow and block traffic using custom rules
Test connectivity using ICMP (Ping)
Troubleshoot connectivity issues
Implement real-world security scenarios
## ⚙️ Services Used
Azure Virtual Network
Azure Network Security Group
Azure Virtual Machines
## 🔧 Configuration Steps
# 1️⃣ Create Virtual Network
Address space: 10.0.0.0/16
Subnets:
Subnet-1: 10.0.1.0/24
Subnet-2: 10.0.2.0/24
# 2️⃣ Deploy Virtual Machines
VM1 → Subnet-1
VM2 → Subnet-2
OS: Windows Server
# 3️⃣ Create NSG
Create NSG and attach to:
Subnet OR
Network Interface (NIC)
# 4️⃣ Configure NSG Rules
# ✅ Allow Rule (Example)
Property	Value
Name	Allow-Ping
Priority	100
Protocol	ICMP
Source	Any
Destination	Any
Action	Allow
## ❌ Deny Rule (Example)
Property	Value
Name	Deny-All
Priority	200
Protocol	Any
Source	Any
Destination	Any
Action	Deny
## 🔍 Testing Scenarios
🔹 Scenario 1: Ping Allowed
Enable ICMP rule
Verify:
ping <Private-IP>

✔ Ping successful

🔹 Scenario 2: Ping Blocked
Add Deny rule with higher priority
✔ Ping fails
🔹 Scenario 3: Priority Check
Lower number = higher priority
Example:
Priority 100 → Allow
Priority 200 → Deny

✔ Rule with priority 100 is applied

## 🛠️ Troubleshooting
Issue	Cause	Fix
Ping not working	ICMP blocked	Allow ICMP in NSG
Still not working	Windows Firewall	Enable ICMP
Rule not applied	Wrong priority	Adjust priority
Traffic not blocked	Lower priority rule	Increase priority
## 🧠 Key Learnings
NSG rules are priority-based
Lower number = higher priority
NSG can be applied at:
Subnet level
NIC level
Both NSG and OS firewall affect traffic
Default rules exist and should be considered
## 📊 Real-World Use Case
Restrict SSH/RDP access
Allow only specific IP ranges
Block unauthorized traffic
Secure internal communication
## ✅ Conclusion

This lab provides hands-on experience with Azure NSG, helping understand how to secure cloud infrastructure by controlling traffic flow effectively.

## Author

Satyabrata Sahoo
Azure Administrator (Learning & Hands-on Labs)

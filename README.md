# Subnet-design
# Network Configuration: IP Interfaces Part 1

## Overview
This project involves configuring a network using the IP address block **10.10.10.0/23** assigned by ARIN. You will design a subnet to connect R1, R2, and Kali in **Area 0**, ensuring they can communicate via Ethernet. The subnet must be as small as possible while accommodating the required hosts.

---

## Instructions

### Part 0: Warm-Up (Not for Credit)
Answer the following preliminary questions:
1. **What is the slash notation representation of 255.255.255.0?**
2. **What is the dot-decimal representation of /30?**
3. **What is the smallest subnet size that would accommodate 5 hosts?**
4. **Fill in the blank cells in the table below:**

| VM (Interface) | IP Address (CIDR Notation) |
|----------------|----------------------------|
| R1 (eth1)      | [Assigned by Vital system] |
| R2 (eth0)      |                            |
| Kali (eth0)    |                            |

---

### Part 1: Configuring Network Interfaces
1. **For R1 and R2:**

2. **For Kali:**

---

### Part 2: Questions
Answer the following questions:
1. **Why did we choose the /29 subnet mask for Area 0?**  

2. **What entries are currently in R1, R2, and Kali’s ARP tables?**  

3. **Why doesn’t R2 have a table entry for Kali after pinging?**  
---

# Subnet-design
### Lab Project: IP Interfaces - Part 1

---

## Project Overview
This lab project involves configuring IP addresses for R1, R2, and Kali in Area 0. These devices are connected through a shared hub, making them part of the same broadcast and collision domain. The objective is to create an appropriate IP subnet to enable communication between these devices while minimizing the subnet size.

---

## Objectives
- Assign IP addresses from the 10.10.10.0/24 subnet to R1, R2, and Kali.
- Configure a subnet large enough for Area 0, but no larger than necessary.
- Verify connectivity between the devices.

---

## Lab Tasks

### 1. **Subnet Calculation and Address Assignment**
   - Determine the smallest subnet size that accommodates the three devices.
   - Fill in the IP address table:

     | VM (Interface) | IP Address (CIDR Notation) |
     |----------------|----------------------------|
     | R1 (eth1)      |                            |
     | R2 (eth0)      |                            |
     | Kali (eth0)    |                            |

---

### 2. **Configuring Network Interfaces**

#### For R1 and R2:
1. Open a terminal and use `vtysh` to configure the interfaces:
   ```bash
   sudo su
   vtysh
   configure terminal
   interface <interface name>
   ip address <IP Address>/<Subnet Mask>
   end
   write
   exit
   ```
2. Verify the configuration using:
   ```bash
   ifconfig
   ```

#### For Kali:
1. Edit the `/etc/network/interfaces` file:
   ```bash
   sudo su
   nano /etc/network/interfaces
   ```
2. Add the following entries:
   ```
   auto eth0
   iface eth0 inet static
   address <IP Address>
   netmask <Subnet Mask>
   network <Network Address>
   broadcast <Broadcast Address>
   ```
3. Save the file and reboot Kali:
   ```bash
   reboot
   ```

---

### 3. **Testing Connectivity**
   - Use the `ping` command to verify communication between the devices:
     ```bash
     ping <Target IP Address>
     ```
   - Confirm successful responses from R1, R2, and Kali.

---

### 4. **ARP Table Verification**
   - Use the `arp` command to inspect the Address Resolution Protocol (ARP) table on each device:
     ```bash
     arp -a
     ```
   - Verify entries for R1, R2, and Kali.

---

## Deliverables
1. Completed IP address table.
2. Screenshot of the configuration files from R1, R2, and Kali.
3. Screenshot showing successful pings between all devices.
4. ARP table entries from R1, R2, and Kali.

---

## Notes
- Ensure the subnet is as small as possible while accommodating all devices.
- Save configurations to prevent data loss after reboots.
- Use `man ifconfig` or `man arp` for additional command details.

---


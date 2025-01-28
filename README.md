# Subnet-design
# README for IP Interfaces: Part 1


### Overview
This project involves configuring IP interfaces for a network using a super-C address block of `10.10.10.0/23` assigned by ARIN. You will subnet the `10.10.10.0/24` block for configuring R1, R2, and Kali in Area 0. These devices are connected via a hub, meaning they are in the same broadcast and collision domain. The goal is to create a minimal and efficient subnet while ensuring all three devices can communicate with each other.

---

### Part 0: Warm-Up (Not for Credit)
Answer the following:
1. What is the slash notation for `255.255.255.0`?
2. What is the dot-decimal representation of `/30`?
3. What is the smallest subnet size to accommodate 5 hosts?
4. Complete the table:

| VM (interface) | IP Address (CIDR Notation) |
|----------------|----------------------------|
| R1 (eth1)      |                            |
| R2 (eth0)      |                            |
| Kali (eth0)    |                            |

---

### Part 1: Configuring Network Interfaces

1. **For R1 and R2**:
   - Open a terminal:
     ```bash
     sudo su
     vtysh
     configure terminal
     interface <interface name> # Replace <interface name> with eth0, eth1, or eth2
     ip address x.x.x.w/29 # Replace x.x.x.w with the assigned IP
     end
     write
     exit
     ```
   - Verify configuration with:
     ```bash
     ifconfig
     ```

2. **For Kali**:
   - Configure the network interface:
     ```bash
     sudo su
     nano /etc/network/interfaces
     ```
   - Add the following lines:
     ```
     auto eth0
     iface eth0 inet static
     address x.x.x.w
     netmask A.A.A.B # Replace A.A.A.B with the converted netmask
     network x.x.x.y
     broadcast x.x.x.z
     ```
   - Save and exit.
   - Reboot Kali:
     ```bash
     reboot
     ```

---

### Part 2: Questions

Answer the following after completing configuration:

1. **Why did we choose the `/29` subnet mask for Area 0?**
2. **Using the Linux `arp` command**, list the current entries in the ARP tables for R1, R2, and Kali.
3. **Ping R2 and Kali from R1**, then analyze the changes in ARP tables. Explain why R2 is aware of R1 but doesn’t have an ARP table entry for Kali.

---

### Submission Requirements

1. **Configuration Files**:
   - Screenshot of `/etc/frr/frr.conf` from R1 and R2.
   - Screenshot of `/etc/network/interfaces` from Kali.

2. **Ping Tests**:
   - Screenshot showing successful ping between R1, R2, and Kali.

3. **ARP Tables**:
   - Screenshot of the ARP tables from R1, R2, and Kali.

4. **Question Answers**:
   - Written answers to Part 3a-3c.

---

### Notes
- Ensure you assign the smallest subnet necessary for Area 0.
- Verify that all devices can communicate with each other before capturing screenshots.
- Follow the provided IP address allocation to avoid conflicts.

Good luck!

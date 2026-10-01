# 3 - VLANs

## Overview

After establishing the basic Ethernet and switching environment, the next challenge was to separate the different departments within the office network.

In the initial network design, all devices shared the same Layer 2 broadcast domain. This allowed broadcast traffic to reach devices across different departments, creating unnecessary traffic and providing limited network segmentation.

To address this, I implemented **Virtual Local Area Networks (VLANs)** on the Cisco switch to logically separate the office into four departmental networks:

- **VLAN 10 — Tech**
- **VLAN 20 — Business Development**
- **VLAN 30 — Finance**
- **VLAN 40 — Admin**

This lab focuses on VLAN creation, naming, port assignment, and verification.

---

## Problem

Without VLANs, all departments operate within the same Layer 2 broadcast domain. Broadcast traffic from one department can reach devices in other departments, which can increase unnecessary network traffic, affect network performance, and reduce network segmentation.

---

## Objective

The objectives of this lab were to:

- Create separate VLANs for each department
- Assign switch ports to the appropriate VLAN
- Verify VLAN membership and configuration
- Demonstrate that broadcast traffic is contained within its VLAN
- Establish a foundation for future trunking and inter-VLAN routing

---

## Network Design

| VLAN | Department | Devices |
|------|------------|---------|
| 10 | Tech | 4 PCs |
| 20 | Business Development | 3 PCs |
| 30 | Finance | 2 PCs |
| 40 | Admin | 2 PCs |

### Port Assignment

```text
Fa0/1 - Fa0/4   → VLAN 10 - TECH
Fa0/5 - Fa0/7   → VLAN 20 - BIZDEV
Fa0/8 - Fa0/9   → VLAN 30 - FINANCE
Fa0/10 - Fa0/11 → VLAN 40 - ADMIN
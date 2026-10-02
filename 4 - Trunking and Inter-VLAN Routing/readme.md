# 4 - Trunking & Inter-VLAN Routing

## Overview

In the previous section, VLANs were implemented to separate the four departments of the office network into distinct Layer 2 broadcast domains:

- **VLAN 10 — Tech**
- **VLAN 20 — Business Development**
- **VLAN 30 — Finance**
- **VLAN 40 — Admin**

This successfully contained broadcast traffic within each VLAN and improved logical network segmentation. However, VLAN separation also meant that devices in different VLANs could no longer communicate directly at Layer 2.

In a real office environment, some communication between departments is still necessary. For example, a workstation in Tech may need to access a shared resource located in Finance, or users from different departments may need to reach services hosted on another subnet.

To address this, this section implements **802.1Q trunking and inter-VLAN routing using Router-on-a-Stick**.

The existing single-switch topology was retained to keep the design efficient for the small-company environment. Instead of adding unnecessary switching infrastructure, a single link between the Cisco 2960 switch and Cisco 2911 router is used to carry traffic for all four VLANs.

---

## Problem

VLANs successfully isolate the departments into separate Layer 2 broadcast domains, but this separation also prevents direct communication between devices belonging to different VLANs.

A mechanism is therefore required to:

1. Carry traffic from multiple VLANs across a single physical link.
2. Provide a gateway for each VLAN.
3. Route traffic between the different departmental subnets when communication is necessary.

---

## Objective

The objectives of this lab were to:

- Configure an 802.1Q trunk between the switch and router.
- Configure Router-on-a-Stick using router subinterfaces.
- Assign a default gateway to each VLAN.
- Enable communication between devices in different VLANs.
- Maintain the logical segmentation established in the previous VLAN section.
- Verify the operation of trunking and inter-VLAN routing.

---

## Network Design

The existing topology consists of one Cisco 2960 switch connected to a Cisco 2911 router.

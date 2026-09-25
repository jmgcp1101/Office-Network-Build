# Ethernet & Switching

## Overview

This project builds upon the IP subnetting design established in the previous stage of the **Office Network Build**.

The network consists of four departments — **Technology, Business Development, Finance, and Administration** — with each department assigned its own IP subnet. All endpoints are currently connected to a single Cisco switch, providing a practical environment for examining how devices communicate through Ethernet and Layer 2 switching.

The objective of this phase is to understand and demonstrate how a switch learns MAC addresses, forwards Ethernet frames, handles broadcast traffic, and supports communication between devices within the local network.

## Objectives

- Understand Ethernet communication and MAC addressing
- Examine Ethernet frame behavior
- Observe ARP address resolution
- Demonstrate MAC address learning
- Analyze the switch's MAC address table
- Observe known-unicast forwarding
- Observe unknown-unicast flooding
- Analyze broadcast traffic
- Understand the relationship between ARP, Ethernet, and ICMP
- Distinguish Layer 2 switching from Layer 3 routing

## Network Topology

The existing office network from the subnetting phase was retained for this project.

- **1 × Cisco 2911 Router**
- **1 × Cisco Switch**
- **11 × PCs**
- **4 × Departments**
  - Technology — 4 PCs
  - Business Development — 3 PCs
  - Finance — 2 PCs
  - Administration — 2 PCs

All PCs are physically connected to the same switch, while each department remains assigned to its respective IP subnet.

## Experiments

The following experiments were conducted using Cisco Packet Tracer:

1. **Baseline Connectivity**
   - Verified communication between devices within the same subnet.

2. **MAC Address Investigation**
   - Identified the MAC addresses of connected devices.

3. **MAC Address Learning**
   - Observed how SW1 dynamically learns MAC addresses and associates them with switch ports.

4. **ARP Resolution**
   - Observed ARP requests and replies during initial communication.

5. **Known-Unicast Forwarding**
   - Examined how the switch forwards frames when the destination MAC address is already known.

6. **Unknown-Unicast Flooding**
   - Observed switch behavior when the destination MAC address is not present in the MAC address table.

7. **Broadcast Traffic**
   - Observed how broadcast frames, including ARP requests, are propagated through the Layer 2 network.

8. **Ethernet and ICMP Traffic Analysis**
   - Used Packet Tracer Simulation Mode to observe the relationship between Ethernet, ARP, and ICMP.

9. **Inter-Subnet Connectivity**
   - Tested communication between devices belonging to different IP subnets and identified the need for Layer 3 routing.

## Key Findings

The experiments demonstrated that:

- Switches use MAC addresses to make Layer 2 forwarding decisions.
- A switch dynamically learns source MAC addresses from incoming Ethernet frames.
- ARP resolves IPv4 addresses to MAC addresses before local Ethernet communication can occur.
- Broadcast and unknown-unicast traffic can be flooded through the Layer 2 network.
- Known-unicast traffic can be forwarded directly to the appropriate switch port.
- Devices in different IP subnets require Layer 3 routing to communicate.

## Documentation

Detailed procedures, observations, screenshots, and analysis are available in:

**[Ethernet & Switching Documentation](documentation/Ethernet-and-Switching.pdf)**

## Project File

- `topology.pkt` — Cisco Packet Tracer topology used for the experiments.

## Next Stage

The next phase of the Office Network Build will introduce **VLANs** to logically segment the four departments and provide separate Layer 2 broadcast domains.
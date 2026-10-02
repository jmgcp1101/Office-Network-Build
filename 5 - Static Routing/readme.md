# 5 - Static Routing

## Overview

In the previous section, trunking and inter-VLAN routing were implemented to allow communication between the different departmental VLANs within the main office.

As the company's infrastructure developed, an additional space within the same building was converted into a dedicated server room. This allowed important company resources to be centralized and accessed by users across the organization.

The server network contains resources supporting the company's operations, including:

- Local storage for selected Disaster Risk Reduction monitoring data
- A company-wide inventory application
- Centralized file storage for different departments

Because the server room operates on a separate IP network from the main office, the routers must be configured with routes that allow traffic to reach networks that are not directly connected.

This section introduces **static routing**, where routes are manually configured to establish communication between the main office network and the server network.

---

## Problem

PCs in the main office can communicate with their local VLANs and other departmental VLANs through inter-VLAN routing. However, the newly established server network is located behind a different router and uses a separate IP network.

Without a route to the server network, the main office router has no information about where to forward traffic destined for those servers.

This creates the need for a routing mechanism that connects the two networks.

---

## Objective

The objectives of this lab were to:

- Establish a separate network for the server room
- Configure a point-to-point transit network between R1 and R2
- Configure IP addressing on the router interfaces
- Configure static routes between the main office and server network
- Provide a return path for traffic
- Verify end-to-end connectivity between office users and centralized server resources

---

## Network Design

### Main Office Network

The main office continues to use the `192.168.100.0/24` address allocation, which was previously divided into departmental VLANs.

| VLAN | Department | Network | Gateway |
|------|------------|---------|---------|
| 10 | Tech | `192.168.100.0/29` | `192.168.100.1` |
| 20 | Business Development | `192.168.100.8/29` | `192.168.100.9` |
| 30 | Finance | `192.168.100.16/29` | `192.168.100.17` |
| 40 | Admin | `192.168.100.24/29` | `192.168.100.25` |

### R1–R2 Transit Network

A dedicated `/30` subnet was used for the point-to-point connection between the two routers.

| Device | IP Address |
|--------|------------|
| R1 | `192.168.102.1/30` |
| R2 | `192.168.102.2/30` |

The `192.168.102.0/30` subnet provides two usable IP addresses, making it suitable for a point-to-point connection between R1 and R2.

### Server Network

The server room uses a separate `192.168.101.0/24` network.

| Device | IP Address | Purpose |
|--------|------------|---------|
| R2 | `192.168.101.1` | Server Network Gateway |
| Data Server | `192.168.101.10` | Local monitoring data |
| Inventory Application Server | `192.168.101.20` | Company inventory system |
| File Server | `192.168.101.30` | Department file storage |

---

## IP Address Configuration

The router interfaces connecting R1 and R2 were configured using the `192.168.102.0/30` transit network.

### R1

```cisco
interface <R1-to-R2-interface>
ip address 192.168.102.1 255.255.255.252
no shutdown
exit
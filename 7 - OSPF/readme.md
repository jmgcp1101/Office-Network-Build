# 7 - OSPF

## Overview

In the previous section, static routing and default routing were implemented to establish communication between the different networks within the company's infrastructure.

As the company continued to expand, a second office was acquired within the same building. The new office is located beside the main office and requires connectivity to the existing network infrastructure and centralized server room.

The existing server room remains inside the main office and contains important company resources, including:

- Local storage for selected Disaster Risk Reduction monitoring data
- A company-wide inventory application
- Centralized file storage for different departments

The new office introduces additional networks that must communicate with the main office and server network.

While static and default routes can successfully provide connectivity, manually configuring routes becomes increasingly difficult to maintain as the network grows.

This section introduces **Open Shortest Path First (OSPF)**, a dynamic routing protocol that allows routers to automatically exchange routing information and learn the available networks within the company's infrastructure.

---

## Problem

Before implementing OSPF, the company's routers relied on manually configured static routes and default routes to reach remote networks.

Although these routes successfully provided connectivity, every new network or routing change required administrators to manually configure the appropriate routes on the routers.

With the addition of the second office, the network now contains multiple LAN networks and router-to-router transit networks.

Manually maintaining routes across an expanding topology can become difficult and increases the possibility of configuration errors.

This creates the need for a dynamic routing protocol that can automatically discover and maintain routes between the different networks.

---

## Objective

The objectives of this lab were to:

- Expand the existing network by adding a second office
- Establish connectivity between the main office, server room, and second office
- Remove the existing static and default routes
- Configure OSPF on all routers
- Use a single OSPF Area 0 for the entire topology
- Advertise the directly connected networks through OSPF
- Establish OSPF neighbor relationships between routers
- Verify dynamically learned routes in the routing table
- Verify end-to-end connectivity using ping and traceroute
- Demonstrate how OSPF automatically learns remote networks and their subnets

---

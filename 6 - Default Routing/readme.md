Default Routing
Overview

This section continues the Office Network Build project after implementing static routing.

As the network grows, manually configuring a specific static route for every destination can become difficult to maintain. To address this, default routing was introduced to provide a route of last resort for destinations that are not explicitly listed in the routing table.

What I Did
Removed the specific static route to the remote server network.
Configured a default route on the router.
Used the existing 192.168.102.0/30 transit network between the routers.
Verified the routing table using show ip route.
Tested connectivity from different departmental PCs to the remote servers.
Reconfigured the routers with both static and default routes to compare their behavior.
Default Route

The default route configured on R1 was:

ip route 0.0.0.0 0.0.0.0 192.168.102.2

This tells R1 to forward traffic to R2 whenever there is no more specific route available for the destination.

Static Route vs Default Route

A static route provides a specific path to a known destination network, while a default route provides a general path for destinations that are not specifically listed in the routing table.

The static route was temporarily removed to demonstrate how the default route could still provide connectivity to the remote server network.

Result

After configuring the default route, PCs from the different departmental networks were successfully able to reach the servers located on the remote network.

This confirmed that R1 was able to use the default route to forward traffic through R2 when no specific route to the destination was present.

Key Takeaway

Default routing provides a simpler way to handle unknown or external destinations without requiring a separate static route for every network.

However, having both a static route and a default route does not automatically provide redundancy. True routing redundancy requires an alternative path that can be used when the primary path becomes unavailable.

Next Step

The next stage of the project will be Dynamic Routing, where routers will learn and exchange network routes automatically.
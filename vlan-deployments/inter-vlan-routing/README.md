# Router-on-a-Stick (Inter-VLAN Routing)

## Objective
Enable communication between VLANs using a single router interface with subinterfaces and 802.1Q encapsulation.

---

## Scenario

Previously, VLANs were isolated at Layer 2.  
In this lab, a router is introduced to provide Layer 3 routing between:

- VLAN 10 (HR)
- VLAN 20 (IT)
- VLAN 30 (Finance)

---

## Devices Used

- 1 × Router (R1)
- 2 × Cisco 2960 Switches
- 6 × PCs

---

## Implementation Summary

- Configured trunk between SW1 and Router
- Created router subinterfaces
- Applied 802.1Q encapsulation
- Assigned gateway IP addresses
- Configured default gateways on PCs
- Verified inter-VLAN communication

---

## Result

Successful routing between VLANs achieved.  
All departments can now communicate via the router.

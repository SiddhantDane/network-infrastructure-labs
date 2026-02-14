# Multi-VLAN Office Network Deployment

## Objective
Implement Layer 2 network segmentation using VLANs across two switches to isolate departmental traffic within a small office environment.

---

## Scenario

A small office network requires logical separation between three departments:

- HR
- IT
- Finance

Each department must be isolated at Layer 2 while still allowing VLAN propagation across multiple switches using trunking.

---

## Devices Used

- 2 × Cisco 2960 Switches
- 6 × PCs
- 1 × Trunk link between switches

---

## VLAN Plan

| VLAN ID | Department | Network |
|---------|------------|----------|
| 10      | HR         | 192.168.10.0/24 |
| 20      | IT         | 192.168.20.0/24 |
| 30      | Finance    | 192.168.30.0/24 |

---

## Implementation Summary

- Created VLAN 10, 20, and 30 on both switches
- Assigned access ports to respective VLANs
- Configured trunk link between switches
- Verified VLAN database consistency
- Tested communication behavior

---

## Configuration Highlights

### VLAN Creation

vlan 10
name HR

vlan 20
name IT

vlan 30
name FINANCE


### Access Port Assignment

interface fa0/x
switchport mode access
switchport access vlan <VLAN_ID>


### Trunk Configuration

interface fa0/24
switchport mode trunk


---

## Verification Commands

show vlan brief
show interfaces trunk


### Connectivity Testing

- Same VLAN communication → Successful
- Cross VLAN communication → Blocked (Expected behavior)

---

## Result

VLAN segmentation was successfully implemented.  
Devices within the same VLAN communicated correctly, while inter-VLAN traffic was restricted, confirming proper Layer 2 isolation.

---

## Key Learning

- VLANs create separate broadcast domains
- Trunk links carry multiple VLANs between switches
- Access ports bind endpoints to specific VLANs
- Proper VLAN design improves security and organization

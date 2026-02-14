# Troubleshooting Notes

## Scenario

After initial configuration, devices in VLAN 10 on Switch 1 were unable to communicate with devices in VLAN 10 on Switch 2.

Expected behavior:
Devices within the same VLAN should communicate successfully across switches via trunk link.

Actual behavior:
Ping requests between HR PCs connected to different switches were failing.

---

## Investigation Steps

### 1. Verified VLAN Creation

Command:
show vlan brief

Result:
VLAN 10, 20, and 30 existed on both switches.

Conclusion:
VLAN database was correct.

---

### 2. Checked Trunk Configuration

Command:
show interfaces trunk

Result:
Switch 1 showed trunk active on Fa0/24.
Switch 2 did NOT show trunk active.

Issue Identified:
Trunk mode was not configured on Switch 2.

---

## Root Cause

The trunk link was configured only on Switch 1.
Switch 2 interface Fa0/24 was still operating in default access mode.

As a result, VLAN tags were not being carried between switches.

---

## Resolution

Configured trunk mode on Switch 2:

interface fa0/24
switchport mode trunk

After applying configuration:

show interfaces trunk

Confirmed trunk status active on both switches.

---

## Verification After Fix

Ping tests performed:

- HR PC (Switch 1) → HR PC (Switch 2) : SUCCESS
- IT PC (Switch 1) → IT PC (Switch 2) : SUCCESS
- HR → IT : FAILED (Expected behavior)

VLAN segmentation and trunking now functioning correctly.

---

## Key Lesson

Both ends of a trunk link must be explicitly configured.
Layer 2 misconfiguration on one side can silently break VLAN propagation.

# Troubleshooting Notes

## Issue
Inter-VLAN communication was not working initially.

## Investigation Steps
1. Verified VLAN configuration on both switches.
2. Checked trunk configuration between SW1 and SW2.
3. Verified router subinterface configuration.
4. Ran `show ip interface brief` on R1.

## Root Cause
The physical interface Gig0/0 on R1 was administratively down.

## Resolution
Enabled the interface:

interface gig0/0
no shutdown

After enabling, subinterfaces became operational.

## Verification After Fix
- HR1 → IT1: SUCCESS
- HR1 → FIN1: SUCCESS
- IT1 → FIN2: SUCCESS

## Lesson Learned
Router-on-a-stick requires:
- Trunk configuration on switch port facing router
- Subinterfaces with correct dot1Q tagging
- Physical interface enabled
- Correct default gateway on PCs

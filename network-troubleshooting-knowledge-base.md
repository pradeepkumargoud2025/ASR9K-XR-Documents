# 🚀 Network Troubleshooting Quick Reference Guide

---

# 1️⃣ IOS Upgrade Issues

## Verification Steps

- ✅ Verify USB/Pen Drive is detected by the router
- ✅ Confirm the correct IOS image is present
- ✅ If USB is not detected properly, format and re-copy the image
- ✅ Ensure the USB is connected to the correct port
- ✅ If the image is visible but boot fails, try another supported USB device

## Password Recovery (Incorrect Password)

- ✅ Verify USB and IOS image availability
- ✅ Power cycle the router
- ✅ Press **ESC** during boot to enter Boot Manager
- ✅ Select the USB image and boot the router

---

# 2️⃣ Interface Down Troubleshooting

## Layer-1 Checks

- ✅ Verify interface is administratively up
- ✅ Check physical patching
- ✅ Verify optical power levels
- ✅ Swap TX/RX if receive power is not detected
- ✅ Perform self-loop test
- ✅ Verify SFP health
- ✅ Replace patch cord if required
- ✅ If all checks pass and interface remains down, investigate hardware/port issues

---

# 3️⃣ Interface Up but No Reachability

## Layer-2 / Layer-3 Verification

- ✅ Verify IP address and subnet mask
- ✅ Check for duplicate IP addresses
- ✅ Verify VLAN/Encapsulation configuration
- ✅ Confirm Layer-2 connectivity
- ✅ Validate xConnect / L2VPN configuration (if applicable)
- ✅ Verify end-to-end patching
- ✅ Check ARP entries
- ✅ Verify MAC address learning

---

# 4️⃣ SSH / Telnet Access Issues

## Management Connectivity Checks

- ✅ Verify SSH/Telnet configuration
- ✅ Check VTY access policies
- ✅ Verify Management VRF reachability
- ✅ Confirm ACLs are not blocking access
- ✅ Validate routing toward the management network

---

# 5️⃣ IS-IS Neighbor Not Forming

## Adjacency Verification

- ✅ Check MTU consistency
- ✅ Verify IS-IS circuit type
- ✅ Validate NET ID
- ✅ Verify Area ID
- ✅ Check authentication configuration
- ✅ Verify interface patching
- ✅ Confirm interface participation in IS-IS

---

# 6️⃣ MPLS LDP Neighbor Down

## LDP Verification

- ✅ Verify MPLS is enabled on the interface
- ✅ Confirm LDP Router-ID reachability
- ✅ Verify Loopback reachability
- ✅ Check authentication settings
- ✅ Validate LDP configuration on both ends
- ✅ Confirm underlying IGP reachability

---

# 7️⃣ BGP Neighbor Down

## BGP Session Checks

- ✅ Verify neighbor IP address
- ✅ Validate AS numbers
- ✅ Check update-source configuration
- ✅ Verify route policies
- ✅ Validate prefix filters
- ✅ Confirm underlying IGP reachability
- ✅ Check ACL / Firewall policies

---

# 8️⃣ Server Reachability Issues

## End-to-End Connectivity Validation

- ✅ Verify server IP configuration
- ✅ Check route advertisement
- ✅ Validate routing tables on Aggregation/Core devices
- ✅ Confirm security policies are not blocking traffic
- ✅ Perform end-to-end traceroute

---

# 9️⃣ Pseudowire / Ring Closure Issues

## L2VPN Verification

- ✅ Verify MTU consistency
- ✅ Check VLAN encapsulation
- ✅ Validate transport mode configuration
- ✅ Confirm pseudowire parameters match on both ends

---

# 🔟 MPLS-TE Tunnel Down

## Traffic Engineering Verification

- ✅ Verify tunnel destination reachability
- ✅ Check explicit-path configuration
- ✅ Validate RSVP signaling
- ✅ Confirm available path resources
- ✅ Verify no fiber cuts or transport issues
- ✅ Check administrative groups
- ✅ Verify affinity settings

---

# 🎯 Golden Troubleshooting Rule

```text
Physical Layer
      ↓
Data Link Layer
      ↓
IP Connectivity
      ↓
IGP Verification
      ↓
MPLS/LDP Verification
      ↓
BGP Verification
      ↓
Service Verification
```

**Always troubleshoot from Bottom → Up**

1. Physical Layer (Fiber / SFP / Power)
2. Layer 2 (VLAN / MTU / Encapsulation)
3. Layer 3 (IP / ARP / Routing)
4. IGP (OSPF / IS-IS)
5. MPLS / LDP
6. BGP
7. Services (L2VPN, L3VPN, TE, Internet)

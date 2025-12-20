## Overview ##

The ASR9000 is a modular, carrier-grade router running IOS-XR, designed for high-performance forwarding and service provider networks.

It includes:

* Line card behavior & synchronization
* RSP control and data plane roles
* Fabric operation & traffic forwarding
* High availability & ISSU
* MPLS, EVPN, L2VPN forwarding
* Operational insights

## ASR9000 Architecture ##
             +----------------+
             |      RSP       |
             | Control Plane  |
             +--------+-------+
                      |
       +--------------+---------------+
       |              |               |
     LC0 (NPU)     LC1 (NPU)      LC2 (NPU)
       |              |               |
       +--------------+---------------+
                      |
                  Fabric Plane

Legend:
* RSP: Master of control & programming
* LC/NPU: Forwarding engine
* Fabric: High-speed traffic switching

## Line Card Synchronization ##

* New line cards sync only with RSP, not with other LCs
* RSP programs routing, FIB, MPLS, QoS, ACLs into the LC
* Fabric only forwards packets, no control plane sync between LCs

LC Insertion Flow:

[LC Inserted] --> [Hardware Discovery by RSP] --> [Firmware/FPGA Alignment]
      --> [Control Plane Sync: RIB/FIB/MPLS/QoS/ACLs] --> [Data Plane Programming]
      --> [ACTIVE State: Interfaces UP]

RSP Roles:

Control Plane
* Routing protocols: BGP, OSPF, ISIS
* RIB maintenance & policy enforcement
* QoS, ACL, uRPF configuration
* Line card process supervision
* HA/ISSU coordination

Data Plane:
[ RSP ]  --> Programs FIB / LFIB / MPLS / ACLs / QoS
[LC NPU] --> Forwards traffic based on RSP programming

Programs forwarding tables on NPUs
Loads NPU microcode & firmware
Monitors LC health & fabric traffic

High Availability:

       +-------------------+
       |   RSP0 ACTIVE     |
       +--------+----------+
                |
                v
       +-------------------+
       |   RSP1 STANDBY    |
       +-------------------+

* Standby RSP mirrors control & forwarding state
* Line cards sync with active RSP only
* Enables seamless switchover

Fabric & Packet Flow:

   Packet In
      │
      ▼
 [LC NPU]  -->  [Fabric]  --> [LC NPU]  --> Packet Out
      │            │            │
      │            │            │
   Forwarding tables programmed by RSP

* Fabric is passive switching
* RSP ensures correct path, hashing, and QoS
* Line cards forward packets as instructed

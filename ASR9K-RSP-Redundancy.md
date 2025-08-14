🔄 RSP Redundancy Modes (Pre-SSO) – Cisco ASR9K

Before SSO (Stateful Switchover) was implemented, the ASR9K RSP (Route Switch Processor) supported the following redundancy modes:

1. HSA – High System Availability

In normal operation, the Standby RSP is powered down.

If the Active RSP fails, the Standby RSP boots up, takes over, and reboots the entire router.

This causes a cold restart — all line cards reload, all sessions are dropped.

2. RPR – Route Processor Redundancy

Standby RSP is partially initialized during normal operation.

IOS XR image is loaded (cold boot).

Startup-Config is synced from Active RSP to Standby RSP.

Configuration changes are not synced in real time.

Layer 2 protocols (STP, LACP, PaGP, VTP) and Layer 3 protocols (OSPF, EIGRP) are not running on the Standby RSP.

On Active RSP failure:

Standby reinitializes as Active

Reloads Startup-Config

Reboots all line cards

Full system restart

Failover time: ~2–4 minutes.

3. RPR+ – Route Processor Redundancy Plus

Standby RSP is still partially initialized, IOS XR is loaded.

Startup-Config is synced from Active to Standby RSP.

Configuration changes are synced in real time.

L2/L3 protocols still not initialized on the Standby RSP.

If the Active RSP fails:

No need to reload Standby RSP or line cards

Switchover is faster compared to RPR.

💡 Key point:

HSA = Standby off until failure → Full reboot.

RPR = Standby partly ready, but config not real-time → Slow failover.

RPR+ = Standby partly ready, config real-time → Faster failover, but still not hitless.

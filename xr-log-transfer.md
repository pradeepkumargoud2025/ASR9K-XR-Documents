# Cisco XR: Transferring Admin Tech Logs to XR Plane

1. **In Admin Mode**, check for the file:
   sysadmin-vm:0_RP0# dir harddisk:/showtech/

2. **Copy to XR VM**:
   sysadmin-vm:0_RP0# copy harddisk:/showtech/<filename>.tgz location 0/RP0/CPU0/VM1 harddisk:/showtech/
   admin> copy harddisk:/showtech/<tech-filename>.tgz harddisk:/showtech/<tech-filename>.tgz location 0/RP0/CPU0/VM1

4. **Verify in XR Mode**:
   RP/0/RP0/CPU0:Router# dir harddisk:/showtech/


# VLAN Segmentation (Packet Tracer Lab)

## Objective

To create VLANs on a switch and observe how communication is restricted between different VLANs.

## Topology

- 1 Switch (Cisco 2960)
- 4 PCs
  - PC0, PC1 → VLAN 2 (Office)
  - PC2, PC3 → VLAN 3 (Home)

## Configuration

```
enable
configure terminal

vlan 2
name office

vlan 3
name home
```

```
interface fastEthernet 0/1
switchport mode access
switchport access vlan 2

interface fastEthernet 0/2
switchport mode access
switchport access vlan 2

interface fastEthernet 0/3
switchport mode access
switchport access vlan 3

interface fastEthernet 0/4
switchport mode access
switchport access vlan 3
```

---

## PC Configuration

- All PCs are in the same IP network:
  - Example: 192.168.0.x / 255.255.255.0
- No default gateway required (same network testing)

---

## Testing

- PC0 → PC1 (same VLAN) → ✅ Success
- PC2 → PC3 (same VLAN) → ✅ Success
- PC0 → PC2 (different VLAN) → ❌ Failed

---

## Observations

- Devices in the same VLAN communicated successfully
- Devices in different VLANs could not communicate
- Even though all devices were connected to the same switch, VLAN configuration restricted communication

---

## Things to Remember

1. VLANs behave like separate switches within the same physical switch
2. VLAN IDs typically start from 2 (VLAN 1 is default)
3. Broadcast traffic is allowed only within the same VLAN
4. ARP is a broadcast and is restricted within a VLAN
5. Switch operations (learn, flood, forward) occur only inside a VLAN
6. Communication between different VLANs fails due to isolation
7. Inter-VLAN communication requires a Layer 3 device (Router or L3 Switch)

---

## Learning

1. VLAN Isolation

- VLANs logically divide a switch into multiple broadcast domains
- Devices in different VLANs are isolated even if they are physically connected

---

2. Why Ping Failed Across VLANs

- Frames are not forwarded across VLAN boundaries
- ARP broadcast does not reach other VLAN
- Therefore, destination MAC is never learned

---
Result

Successful communication within VLANs and isolation observed between different VLANs.

# Multiple PCs to Switch Connection (Packet Tracer Lab)

## Objective

To connect multiple PCs using a switch and verify communication within the same network.

## Topology

- 1 Switch (Cisco 2960)
- 6 PCs connected to the switch

## Configuration

| PC | IP Address | Subnet Mask |
|-----|---------------|-----------------|
| PC0 | 192.168.0.2 | 255.255.255.0 |
| PC1 | 192.168.0.3 | 255.255.255.0 |
| PC2 | 192.168.0.4 | 255.255.255.0 |
| PC3 | 192.168.0.5 | 255.255.255.0 |
| PC4 | 192.168.0.6 | 255.255.255.0 |
| PC5 | 192.168.0.7 | 255.255.255.0 |

## Steps Performed

- Connected all PCs to the switch using automatic cable selection
- Assigned IP addresses in the same network
- Tested connectivity using ping
- Observed packet flow in Simulation mode

## Observations

- Initial communication triggered an ARP request (broadcast)
- The switch forwarded the request to all connected PCs
- Only the destination PC responded with its MAC address
- Other PCs discarded the packet
- After ARP resolution, communication became direct (unicast)

## Learning

## 1. MAC Address Table in Switch

- A switch learns MAC addresses dynamically from incoming frames
- Each MAC address is mapped to a specific port

Command used:

enable
show mac address-table

---

## 2. Target MAC vs Destination MAC

Destination MAC:

- Part of the Ethernet frame
- Used to deliver the frame to the correct device
- Can be broadcast (FF:FF:FF:FF:FF:FF) or unicast

Target MAC:

- Part of the ARP request
- Represents the MAC address being searched
- Initially unknown → shown as 0000.0000.0000

---

## 3. Network Communication

- Devices in the same network communicate directly using a switch
- No router is required for same subnet communication

## Result

All PCs were able to successfully communicate with each other.

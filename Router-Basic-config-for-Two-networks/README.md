# Router Based Network Communication (Packet Tracer Lab)

## Objective

To enable communication between two different networks using a router.

## Topology

- 1 Router
- 2 Switches
- 4 PCs (2 in each network)

## Network Configuration

### Network 1

- PC0 → 192.168.1.2
- PC1 → 192.168.1.3
- Router Interface → Gig0/0 → 192.168.1.1

### Network 2

- PC2 → 192.168.2.2
- PC3 → 192.168.2.3
- Router Interface → Gig0/1 → 192.168.2.1

---

## Steps Performed

### 1. Router Configuration (CLI)

Configured router interfaces using CLI:

enable
configure terminal

interface gig0/0
ip address 192.168.1.1 255.255.255.0
no shutdown

interface gig0/1
ip address 192.168.2.1 255.255.255.0
no shutdown

end

---

### 2. PC Configuration

- Assigned IP addresses manually to each PC
- Set default gateway on each PC according to its network:
  - Network 1 → 192.168.1.1
  - Network 2 → 192.168.2.1

---

### 3. Connectivity Testing

- Verified PC to Router communication
- Verified cross-network communication using ping

---

## Observations

- Communication within same network worked directly
- Communication across networks required router
- Router forwarded packets between the two networks successfully

---

## Learning

### 1. Inter-Network Communication

- Devices in different networks cannot communicate directly
- A router is required to forward packets between networks
- Default gateway is used to send traffic outside the local network

---

### 2. Why First Ping Failed (Packet Loss)

- The first ping packet was lost due to initial setup delay

- ARP (Address Resolution Protocol) was used to discover MAC addresses

- The PC first resolved the router’s MAC address

- The router then resolved the destination PC’s MAC address

- Due to this delay, the first ICMP packet timed out

- Subsequent packets succeeded because:
  
  - MAC addresses were already learned
  - Routing path was established

---

Result

Successful communication achieved between devices in different networks using a router.

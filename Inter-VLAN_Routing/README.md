# Inter-VLAN Routing (Router-on-a-Stick)

## Objective

To enable communication between different VLANs using a router and understand VLAN tagging and routing.

---

## Topology

- 1 Switch (Cisco 2960)
- 1 Router
- 4 PCs
  - VLAN 2 → PC0, PC1
  - VLAN 3 → PC2, PC3

---

## Network Configuration

| VLAN   | Network        | Gateway     |
| ------ | -------------- | ----------- |
| VLAN 2 | 192.168.2.0/24 | 192.168.2.1 |
| VLAN 3 | 192.168.1.0/24 | 192.168.1.1 |

---

## Steps Performed

### 1. Configure VLANs on Switch

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

### 2. Configure Trunk Port

```
interface fastEthernet 0/24
switchport mode trunk
```

---

### 3. Configure Router

```
enable
configure terminal

interface gig0/0
no shutdown
```

```
interface gig0/0.2
encapsulation dot1Q 2
ip address 192.168.2.1 255.255.255.0
```

```
interface gig0/0.3
encapsulation dot1Q 3
ip address 192.168.1.1 255.255.255.0
```

---

## Observations

* First ping shows 25% loss
* Due to ARP resolution (PC → Router → Destination)

---

## Learning

* VLANs require different subnets
* Inter-VLAN communication needs a router
* Trunk ports carry multiple VLAN traffic
* Switch adds an 802.1Q VLAN tag to frames on trunk ports so the router can identify which VLAN the traffic belongs to.
* Router uses subinterfaces with VLAN tagging
* ARP causes initial packet delay

---

## Result

Successful communication between VLANs achieved.

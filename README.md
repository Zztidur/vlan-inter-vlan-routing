# VLAN & Inter-VLAN Routing — Cisco Packet Tracer

Implementasi VLAN dan Inter-VLAN Routing menggunakan metode Router-on-a-Stick pada Cisco Packet Tracer.

Project ini membagi jaringan menjadi beberapa VLAN menggunakan VLAN ID 10, 20, dan 30. Routing antar VLAN dilakukan menggunakan subinterface pada Cisco Router dengan encapsulation 802.1Q.

---

## 📌 Project Overview

Project menggunakan tiga jaringan:

| VLAN | Network | Gateway |
|---|---|---|
| VLAN 10 | 192.168.10.0/24 | 192.168.10.1 |
| VLAN 20 | 192.168.20.0/24 | 192.168.20.1 |
| VLAN 30 | 192.168.30.0/24 | 192.168.30.1 |

Router berfungsi sebagai perangkat Layer 3 yang melakukan routing antar VLAN.

---

## 🗺️ Network Topology

```text
                         Router
                           |
                  GigabitEthernet0/0
                           |
                       802.1Q
                         Trunk
                           |
                         Switch
                    _______|_______
                   |       |       |
                VLAN 10 VLAN 20 VLAN 30
                   |       |       |
                  PC      PC      PC
```

---

## 🌐 VLAN Addressing

| VLAN | Network | Default Gateway |
|---|---|---|
| 10 | 192.168.10.0/24 | 192.168.10.1 |
| 20 | 192.168.20.0/24 | 192.168.20.1 |
| 30 | 192.168.30.0/24 | 192.168.30.1 |

---

## ⚙️ Router Configuration

Physical interface:

```text
GigabitEthernet0/0
```

Interface tersebut digunakan sebagai parent interface untuk subinterface VLAN.

### VLAN 10

```text
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
```

### VLAN 20

```text
interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
```

### VLAN 30

```text
interface GigabitEthernet0/0.30
 encapsulation dot1Q 30
 ip address 192.168.30.1 255.255.255.0
```

---

## 🔀 Router-on-a-Stick

Metode Router-on-a-Stick digunakan untuk melakukan routing antar VLAN melalui satu physical interface router.

Pada project ini:

```text
Gi0/0.10 → VLAN 10 → 192.168.10.1
Gi0/0.20 → VLAN 20 → 192.168.20.1
Gi0/0.30 → VLAN 30 → 192.168.30.1
```

Encapsulation yang digunakan:

```text
802.1Q
```

---

## 🔍 Interface Verification

Verifikasi dilakukan menggunakan:

```text
show ip interface brief
```

Hasil menunjukkan:

```text
GigabitEthernet0/0.10  192.168.10.1  up  up
GigabitEthernet0/0.20  192.168.20.1  up  up
GigabitEthernet0/0.30  192.168.30.1  up  up
```

Hal tersebut menunjukkan ketiga subinterface aktif.

---

## 🧪 Inter-VLAN Connectivity Testing

Pengujian dilakukan menggunakan `ping`.

### VLAN 10 Gateway

```text
ping 192.168.10.1
```

Result:

```text
Sent     = 4
Received = 4
Lost     = 0 (0% loss)
```

### VLAN 20 Client

```text
ping 192.168.20.10
```

Result:

```text
Sent     = 4
Received = 4
Lost     = 0 (0% loss)
```

### VLAN 30 Client

```text
ping 192.168.30.10
```

Result:

```text
Sent     = 4
Received = 4
Lost     = 0 (0% loss)
```

---

## 📊 Testing Summary

| Destination | Result | Packet Loss |
|---|---|---:|
| 192.168.10.1 | Success | 0% |
| 192.168.20.10 | Success | 0% |
| 192.168.30.10 | Success | 0% |

---

## 🔍 Verification Commands

### Interface

```text
show ip interface brief
```

### Configuration

```text
show running-config
```

### Connectivity

```text
ping <destination-ip>
```

---

## 📂 Repository Structure

```text
vlan-inter-vlan-routing/
│
├── config/
│   ├── router.txt
│   └── test ping.txt
│
├── topology.png
├── project-3-Vlan-routing.pkt
└── README.md
```

---

## 🎯 Project Objectives

Project ini bertujuan untuk memahami:

- VLAN
- VLAN segmentation
- VLAN ID
- 802.1Q
- Router-on-a-Stick
- Router subinterface
- Inter-VLAN Routing
- IPv4 addressing
- Connectivity testing
- Network troubleshooting

---

## 🛠️ Tools & Technologies

- Cisco Packet Tracer
- Cisco Router
- Cisco Switch
- VLAN
- 802.1Q
- Router-on-a-Stick
- IPv4
- ICMP/Ping
- Cisco IOS CLI

---

## 📚 Learning Outcome

Melalui project ini, saya mempraktikkan segmentasi jaringan menggunakan VLAN dan implementasi Inter-VLAN Routing menggunakan Router-on-a-Stick dengan encapsulation 802.1Q.

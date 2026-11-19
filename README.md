# Small Enterprise Office

_Level: foundation — Enterprise Campus & LAN — Switching · SVIs · DHCP · Static Routing_

**Status: Verified.** Completed on 2026-11-19; every requirement was machine-checked against the network built in BuildTheNet and passed.

Snapshot taken 2026-11-19. Built in a simulation — no physical or production equipment was involved.

## Scenario

Corran Surveyors has outgrown its single 24-port switch: twelve staff, a plotter and a file server on one floor. Add a second switch, join the two without creating a loop, and keep everyone, including the file server, on one addressed subnet behind the router.

### Why it matters

The first design decision an engineer makes is where the second switch goes and how the two are joined. Doing it for a small office, where a loop takes the whole firm offline, is that decision at its smallest scale.

## Requirements

| # | Requirement | Status | Checked by |
|---|---|---|---|
| 1 | Place a router, two switches and at least four hosts. | Passed | Sandbox check |
| 2 | Join the two switches with a single uplink and keep the topology loop-free. | Passed | Sandbox check |
| 3 | Address the office from one subnet, with the router as the gateway. | Passed | Sandbox check |
| 4 | Add a server and confirm every host can reach it. | Passed | Sandbox check |

## Topology

![Topology diagram](topology.svg)

## Addressing

| Device | Interface | Address | Mask | Mode | Gateway |
|---|---|---|---|---|---|
| R1 | Gi0/0 | 192.168.1.1/24 | 255.255.255.0 | routed |  |
| SE1 | Eth0 | 192.168.1.10/24 | 255.255.255.0 | VLAN 1 | 192.168.1.1 |
| PC-1 | Eth0 | 192.168.1.11/24 | 255.255.255.0 | VLAN 1 | 192.168.1.1 |
| PC-2 | Eth0 | 192.168.1.12/24 | 255.255.255.0 | VLAN 1 | 192.168.1.1 |
| PC-3 | Eth0 | 192.168.1.13/24 | 255.255.255.0 | VLAN 1 | 192.168.1.1 |
| PC-4 | Eth0 | 192.168.1.14/24 | 255.255.255.0 | VLAN 1 | 192.168.1.1 |

## Device configurations

Running-configs as `show running-config` prints them in the BuildTheNet sandbox. Passwords, secrets, keys and SNMP communities are replaced with `<removed>`.

- [Switch-1](configs/Switch-1.txt)
- [Switch-2](configs/Switch-2.txt)
- [R1](configs/R1.txt)

---

Built on [BuildTheNet](https://www.buildthenet.io/projects/proj-pt-02-small-enterprise)

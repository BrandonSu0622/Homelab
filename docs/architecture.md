# Architecture

## Physical Layout

```
Internet
↓
Sonic Fiber ONT
↓
Eero Gateway Router
│   DHCP, NAT, WiFi, firewall
↓
NETGEAR GS308E 8-Port Managed Switch
├── ThinkPad T440p ── Ubuntu Server ── Docker Host
└── Headless Desktop ── Proxmox VE ── Hypervisor
```

## Service Architecture

```
Client Browser
↓
Nginx Proxy Manager (port 80/443)
│   routes by hostname
├── Pi-hole admin
├── Portainer
├── Uptime Kuma
└── Homepage

Pi-hole (port 53)
│   local DNS resolver
└── resolves .home hostnames → Docker host IP
    └── NPM routes to correct container
```

## Data Flow — Internal Request

```
1. Client requests portainer.home
2. Pi-hole resolves portainer.home → <server-ip>
3. Browser sends HTTP request to <server-ip>:80
4. Nginx Proxy Manager reads Host header
5. NPM forwards to Portainer container on :9000
6. Response returned to client
```

> **Current state:** Steps 2–5 are not yet active. Clients access services directly by IP:port. Pi-hole DNS activation is the next milestone.

## Proxmox Architecture (Planned)

```
Proxmox VE (Headless Desktop)
├── VM: Rocky Linux — sysadmin practice
├── VM: Windows Server 2022 — Active Directory lab
└── VM: TrueNAS SCALE — NAS / storage learning
```

## Kubernetes Architecture (Planned)

```
3x Mini PC Nodes (Beelink SER5 or similar)
├── Node 1: Control plane
├── Node 2: Worker
└── Node 3: Worker

Managed Switch (VLAN-segmented)
├── VLAN 10: Management
└── VLAN 20: Kubernetes pod traffic
```

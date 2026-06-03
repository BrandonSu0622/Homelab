# Homelab

A self-hosted infrastructure lab running on consumer hardware. Built to develop real-world skills in Linux administration, networking, containerization, virtualization, and eventually Kubernetes and AI infrastructure.

---

## Hardware

| Device | Role | OS |
|---|---|---|
| ThinkPad T440p | Primary compute / Docker host | Ubuntu Server |
| Headless Desktop (i5-6600K, 32GB RAM, RX 6600) | Hypervisor | Proxmox VE |

---

## Current Stack

All services run as Docker containers on the ThinkPad. Each service has its own `compose.yml` under `/srv/docker/<service>/`.

```
Ubuntu Server (ThinkPad)
└── Docker Engine
    ├── Portainer          — container management UI
    ├── Nginx Proxy Manager — reverse proxy
    ├── Pi-hole            — local DNS + ad filtering
    ├── Uptime Kuma        — service monitoring
    └── Homepage           — self-hosted dashboard
```

### Network Topology

```
Internet (Sonic Fiber)
↓
ONT
↓
Eero Gateway Router (DHCP, NAT, WiFi)
↓
NETGEAR GS308E Switch
├── ThinkPad Ubuntu Server (Docker host)
└── Headless Desktop (Proxmox)
```

### Service Access

Services are currently accessed by IP:port. Local `.home` hostname routing via Pi-hole + Nginx Proxy Manager is in progress.

---

## Planned Expansion

### Short Term
- [ ] Configure Pi-hole as primary DNS resolver
- [ ] Configure Nginx Proxy Manager proxy hosts for `.home` hostnames
- [ ] Deploy first Proxmox VM (Rocky Linux)
- [ ] Set up Active Directory lab on Proxmox
- [ ] SSH/HTTP Honeypot with OpenCanary (security learning project)
- [ ] NETGEAR GS308E VLAN configuration

### Medium Term
- [ ] Ansible for configuration management and service deployment
- [ ] Prometheus + Grafana monitoring stack
- [ ] TrueNAS on Proxmox for NAS/storage learning
- [ ] Tailscale mesh VPN for secure remote access
- [ ] GitOps workflow with GitHub Actions

### Long Term (Kubernetes & AI Infra)
- [ ] 3-node mini PC cluster (Beelink SER5 or similar)
- [ ] k3s or kubeadm Kubernetes cluster
- [ ] AI inference stack (Ollama / vLLM) leveraging RX 6600 GPU
- [ ] ELK Stack or Loki for centralized logging

---

## Skills Being Developed

- Linux administration (Ubuntu Server, Rocky Linux)
- Docker and Docker Compose
- Networking (DNS, reverse proxies, VLANs, subnetting)
- Virtualization (Proxmox, KVM)
- Infrastructure documentation and runbooks
- Security fundamentals (Pi-hole, firewall, honeypot)
- Kubernetes (planned)
- Infrastructure as Code — Ansible, Terraform (planned)

---

## Certifications

| Cert | Status |
|---|---|
| Google Cybersecurity Professional | ✅ Complete |
| CCNA 200-301 | 🔄 In Progress |
| RHCSA | 📅 Planned |

---

## Docs

- [Architecture](docs/architecture.md)
- [Docker Stack](docs/docker-stack.md)
- [Future Plans](docs/future-plans.md)

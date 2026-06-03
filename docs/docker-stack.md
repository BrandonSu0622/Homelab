# Docker Stack

All containers run on Ubuntu Server (ThinkPad T440p). Each service is managed with its own `docker-compose.yml` under `/srv/docker/<service>/`. Persistent data uses bind mounts — no named volumes.

## Services

### Portainer
Docker management UI. Provides a web interface for managing containers, images, volumes, networks, and logs without needing SSH.

### Nginx Proxy Manager
Reverse proxy handling HTTP/HTTPS routing. Routes incoming requests to the correct container based on the `Host` header. Manages SSL certificates via Let's Encrypt.

### Pi-hole
Network-wide DNS resolver and ad blocker. Acts as the local DNS server — resolves `.home` internal hostnames and filters ad/tracking domains for all devices on the network.

### Uptime Kuma
Self-hosted uptime monitoring. Monitors each service on a schedule and provides a status dashboard with response time history and alerting.

### Homepage
Self-hosted start page with service widgets. Integrates with Portainer, Pi-hole, Uptime Kuma, and Nginx Proxy Manager to display live service stats.

## Directory Convention

```
/srv/docker/
├── portainer/
│   ├── compose.yml
│   └── data/
├── npm/
│   ├── compose.yml
│   ├── data/
│   └── letsencrypt/
├── pihole/
│   ├── compose.yml
│   ├── etc-pihole/
│   └── etc-dnsmasq.d/
├── kuma/
│   ├── compose.yml
│   └── data/
└── homepage/
    ├── compose.yml
    └── config/
```

## Design Decisions

**One compose file per service** — isolates services so one can be restarted or updated without affecting others.

**Bind mounts over named volumes** — all data is visible on the host filesystem and can be backed up with a simple directory copy.

**No services installed on host OS** — the host stays clean. Everything runs in containers.

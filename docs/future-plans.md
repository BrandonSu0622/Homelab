# Future Plans

## Next Milestones

### DNS + Reverse Proxy Activation
Configure Pi-hole as the primary DNS resolver for the network and set up Nginx Proxy Manager proxy hosts. This enables `.home` hostname routing for all internal services instead of IP:port access.

### Proxmox VMs
The headless desktop is running Proxmox VE with no VMs deployed yet. First VMs planned:
- **Rocky Linux** — RHEL-based sysadmin practice environment
- **Windows Server 2022** — Active Directory, GPO, DNS lab
- **TrueNAS SCALE** — NAS and storage protocol learning (NFS, SMB, iSCSI)

### Active Directory Lab
Stand up a Windows Server VM on Proxmox to practice AD administration — users, groups, GPO, DNS integration. This mirrors enterprise environments and is directly relevant to support/infrastructure roles.

### Security Projects
- **SSH/HTTP Honeypot** — Deploy OpenCanary in Docker to observe real-world attack traffic on a public-facing fake SSH/HTTP server. Log and analyze credential attempts.
- **VLAN Segmentation** — Configure VLANs on the NETGEAR GS308E to separate management, workload, and Kubernetes traffic.

## Medium Term

### Automation
- **Ansible** — automate service deployment and configuration management across hosts
- **Terraform** — infrastructure as code for provisioning VMs and cloud resources

### Monitoring Stack
- **Prometheus + Grafana** — replace Uptime Kuma with a full metrics pipeline; build dashboards for CPU, memory, disk, and network per host

### Remote Access
- **Tailscale** — WireGuard-based mesh VPN for secure access to homelab from anywhere without exposing services publicly

## Long Term — Kubernetes Cluster

Planning a 3-node mini PC cluster (Beelink SER5 or similar) for Kubernetes:

- 3x nodes with 32GB RAM and NVMe storage each
- Managed switch with VLAN segmentation (management vs. pod traffic)
- k3s (lightweight) or kubeadm (full upstream) distribution
- GitOps workflow with ArgoCD or Flux

This mirrors enterprise Kubernetes deployments and maps directly to Platform/DevOps and AI Infrastructure engineering roles.

## Long Term — AI Inference Infrastructure

The Proxmox desktop has an AMD RX 6600 (8GB VRAM, RDNA 2). Planned use:

- Pass the GPU through to a VM via Proxmox PCIe passthrough
- Run Ollama or vLLM for local LLM inference
- Explore ROCm (AMD's CUDA equivalent) for GPU-accelerated workloads
- Build toward AI Infrastructure engineering skills

## Certification Roadmap

| Cert | Timeline | Why |
|---|---|---|
| CCNA 200-301 | Late 2026 | Networking foundation — MSP, sysadmin, infrastructure roles |
| RHCSA | 2027 | Enterprise Linux — required for many sysadmin/infra roles |
| CKA (Kubernetes) | 2027–2028 | Platform/DevOps/AI Infra roles |
| AWS/Azure Associate | 2028 | Cloud engineering track |

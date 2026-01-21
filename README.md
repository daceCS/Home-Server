# Home Server Project

A comprehensive self-hosted infrastructure built on Proxmox VE, supporting multi-purpose workloads including software development, cybersecurity research, media streaming, and network storage.

## Project Goals

- Create a robust 24/7 development environment supporting multiple programming languages
- Establish cybersecurity lab capabilities for learning and testing
- Provide reliable network storage and media streaming services
- Enable secure remote access for personal use and selective sharing
- Maintain service isolation and infrastructure stability

## Hardware Specifications

- **CPU**: Intel Core i7-7700
- **GPU**: NVIDIA GeForce RTX 1070
- **RAM**: 32GB
- **Storage**: Hybrid SSD/HDD configuration
  - 256GB NVMe SSD for system and critical services
  - 1TB HDD for bulk storage and media

## Architecture

### Virtualization Platform
- **Proxmox VE** as the hypervisor foundation
- **Ubuntu LXC Containers** for lightweight service isolation
- **Virtual Machines** for heavier workloads requiring full OS isolation

### Network Architecture
```
Internet
    ↓
Router/Firewall
    ↓
    ├─→ Tailscale VPN (Personal Access)
    │       ↓
    │   Home Server (All Services)
    │
    └─→ Nginx Proxy Manager (Selective Public Access)
            ↓
        SSL/TLS (Let's Encrypt)
            ↓
        Public Services (e.g., Jellyfin)
```

## Services & Capabilities

### Development Environment
- **Languages Supported**: Python, JavaScript, Node.js, Java, C++, HTML, CSS
- **Tools**:
  - Git for version control
  - Docker for containerization
  - Python virtual environments (venv)
  - VS Code Remote-SSH integration
  - npm for JavaScript package management

### Media & Storage
- **Jellyfin**: Self-hosted media server with remote access
- **Samba**: Network file sharing across LAN devices
- **Storage Management**: Proper partitioning and mounting for reliability

### Security & Research
- **Kali Linux VM**: Cybersecurity lab environment
- **Tailscale VPN**: Secure private network access
- **Nginx Proxy Manager**: Reverse proxy with SSL certificate automation

## Security Implementation

### Dual-Layer Access Strategy

**Private Access (Tailscale VPN)**
- Full access to all services and infrastructure
- Encrypted peer-to-peer connections
- Personal devices only

**Public Access (Nginx Proxy Manager + Cloudflare Tunnel)**
- Selective exposure of specific services
- SSL/TLS encryption via Let's Encrypt
- Cloudflare Tunnel for secure public access without port forwarding
- Authentication where applicable
- Services like Jellyfin for trusted friends/family

## Current Status

### Completed
- [x] Proxmox VE installation and configuration
- [x] Ubuntu container and VM deployment
- [x] Samba network storage setup
- [x] Jellyfin media server deployment
- [x] Tailscale VPN integration
- [x] Nginx Proxy Manager with SSL certificates
- [x] Docker installation and configuration
- [x] Development tools setup (Git, Node.js, Python)
- [x] Storage partitioning and mounting

### In Progress
- [ ] Hardware transcoding optimization for Jellyfin
- [ ] Backup and disaster recovery solutions

## Technology Stack

**Infrastructure**
- Proxmox VE
- Ubuntu Server
- LXC Containers
- Docker

**Networking & Security**
- Tailscale
- Nginx Proxy Manager
- Let's Encrypt
- Cloudfare Tunnels

**Development**
- Git
- Python 3.x + pip + venv
- Node.js + npm
- VS Code Remote
- Docker Compose

**Services**
- Jellyfin (Media)
- Samba (File Sharing)
- Kali Linux (Security Research)

## Key Learnings

### Infrastructure Principles
1. **Service Isolation**: Dedicated containers/VMs prevent conflicts and improve stability
2. **Storage Strategy**: Internal drives essential for 24/7 reliability; external drives unsuitable for primary storage
3. **Container Types**: Understanding differences between Docker containers and Proxmox LXC containers is crucial
4. **Security Layers**: VPN for trusted access, reverse proxy for controlled public exposure

### Best Practices Implemented
- Python virtual environments for project isolation
- Proper drive mounting and partition management
- Step-by-step methodical approach to infrastructure changes
- Testing in isolated environments before production deployment
- Documentation and version control for configurations

## Skills Developed

- Linux Server Administration
- Virtualization & Containerization
- Network Security & VPN Configuration
- Reverse Proxy & SSL/TLS Management
- Storage Management & Optimization
- Infrastructure Planning & Design
- Remote Access Solutions
- DevOps Practices

## Future Enhancements

### Planned Implementations
  - DNS configuration (SPF, DKIM, DMARC)
  - VLAN configuration
  - SIEM implementation

### Potential Upgrades
- Hardware transcoding for improved Jellyfin performance
- Automated backup solutions (3-2-1 backup strategy)
- Monitoring and alerting systems (Prometheus/Grafana)
- Home automation integration

## Documentation Structure

This repository contains:
- Configuration files and scripts
- Setup guides and tutorials
- Troubleshooting documentation
- Network diagrams and architecture documentation
- Lessons learned and best practices

## Contributing

This is a personal learning project, but suggestions and feedback are welcome! Feel free to open issues for questions or recommendations.

**Note**: This is an active learning project. Configurations and services are continuously evolving as new capabilities are added and optimized.

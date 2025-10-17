# 🏠 HomeLab — Modular Self-Hosted DevOps & AI Stack

**HomeLab** is an open-source, modular Docker Compose collection designed to build your own self-hosted ecosystem — complete with automation, AI tools, dashboards, and developer utilities.  
Each component lives in its own directory for cleaner version control and independent updates.

---

## 📦 Overview

HomeLab helps you quickly spin up production-grade tools on your local or cloud environment using Docker and GitOps.  
It’s built to be **portable**, **maintainable**, and **deployment-ready** through CI/CD pipelines such as **Jenkins**.

### 🧩 Core Modules

| Module | Description |
|:-------|:-------------|
| **N8N** | Powerful low-code workflow automation platform (AI integrations, APIs, DevOps pipelines) |
| **OpenWebUI** | Local AI interface for Ollama or other open LLMs |
| **Portainer** | GUI to manage Docker containers, volumes, and networks |
| **Jenkins** | CI/CD automation for deployment and updates |
| **MediaServer** | Self-hosted streaming and library management (e.g., Jellyfin) |
| **Drive** | Local or cloud-synced storage mount (e.g., Nextcloud integration) |
| **Cloudflare-Tunnel** | Secure remote access to your services via HTTPS without port forwarding |

## ⚙️ Architecture

Each sub-folder contains a self-contained `docker-compose.yml` file with its own `.env` file and persistent volumes.  
This structure allows modular deployment and independent scaling.


---

## 🚀 Quick Start

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/vigneshsivasubramaniyan/HomeLab.git
cd HomeLab
```
### 2️⃣ **Customize Environment Variables**

Each service folder contains an .env.example.
Duplicate it and configure your own secrets, paths, and credentials:
```bash
cp .env.example .env
```
3️⃣ Start Services Individually

To run a single service:
```bash
cd N8N
docker compose up -d
```
---
💡**Use Cases**

⭐ DevOps Automation — Jenkins + n8n pipelines for self-healing deployments
⭐ AI Workbench — Local Ollama + OpenWebUI integration for private AI workflows
⭐ Media Hub — Stream, sync, and manage personal content securely
⭐ Private Cloud — Nextcloud / Drive integration for backup and sync
⭐ HomeLab Dashboard — Centralized monitoring and analytics view

---
⚙️ **Continuous Deployment (via Jenkins)**

Jenkins automates your GitOps cycle:

**Trigger**: Commit changes to the GitHub repo

**Build**: Jenkins pulls the latest commit

**Deploy**: Runs docker compose up -d --build for changed services

**Notify**: Sends build status via Telegram or Email (optional)

A preconfigured Jenkinsfile will handle:

Multi-service deploys

Error rollback

Version tagging (homelab_n8n:v1.0.x)

---
**🛠️ Updating**

Pull the latest images and restart:
```
docker compose pull
docker compose up -d --build
```
Or automate via Jenkins scheduled pipeline.

---
🧠 **Tips**

All persistent data is stored under /data/ volumes in each module.

To access local files in containers, map shared folders:
```
volumes:
  - ./shared:/data/shared
```
Use Portainer to visualize container health and logs easily.
---
📚 **Recommended Setup Stack**
Category	Tool	Purpose
Automation	n8n	Workflow orchestration
AI	OpenWebUI + Ollama	Local language models
CI/CD	Jenkins	Build & deployment automation
Monitoring	Portainer	Docker visualization
Storage	Nextcloud / Drive	File sync and backup
Media	Jellyfin	Stream and organize media
Security	Cloudflare Tunnel	HTTPS remote access

---
****🧰 Future Roadmap**

 Add unified meta docker-compose.yml for entire stack

 Include Traefik reverse proxy for SSL & routing

 Add Grafana dashboard for monitoring

 Integrate Tailscale VPN connectivity

---
** 💬 **Support & Contribution****

💡 **Share Ideas**: Open an Issue or Discussion on GitHub

🧠 **Join the Conversation**: Collaborate on setups and optimizations

🚀 **Contribute:** Fork and submit PRs for new modules or improvements

Maintained with ❤️ by [Vignesh Sivasubramaniyan](https://github.com/vigneshsivasubramaniyan)
Empowering self-hosted automation and AI for everyone.

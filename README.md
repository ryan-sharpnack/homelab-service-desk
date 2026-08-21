# Homelab Service Desk

A self-hosted, production-grade IT Service Desk — GLPI, containerized with Docker, running entirely on my own homelab hardware. Built to demonstrate real ITSM/ITIL practice as part of my transition into IT Support, with a tiered L1 → L2 → L3 progression (100 closed tickets per tier).

## Why GLPI, not a custom app
- Real, production-grade ITSM software actual IT departments run — not a demo app
- Native ITIL structure: Incident / Service Request / Problem / Change built into the tool itself
- Built-in dashboarding (ticket counts, SLA compliance, resolution trends) with no paid plugin required
- Administering it is IT Support / Systems Administration work, matching where I'm positioning my skills

## Architecture
- GLPI (official `glpi/glpi` image) + MySQL, via Docker Compose
- Hosted on a Dell OptiPlex 3040 running Kali Linux
- Ticket tiers modeled as Groups: `L1 - Help Desk`, `L2 - Desktop Support`, `L3 - Systems Administration`
- ITIL Categories: Identity, Hardware, Network, SaaS, Infrastructure
- SLA policy assigned automatically by ticket priority via Business Rules:
  - Urgent: 1 hour · High: 4 hours · Medium: 24 hours · Low: 72 hours

## Status
Infrastructure is fully configured and operational. Currently working Tier 1 (L1 - Help Desk) tickets.

## Running it yourself
\`\`\`bash
git clone https://github.com/ryan-sharpnack/homelab-service-desk.git
cd homelab-service-desk
cp .env.example .env   # edit with your own DB credentials
docker compose up -d
\`\`\`
Visit `http://localhost` — GLPI auto-installs if all five DB variables in `.env` are set.

## Tech stack
Docker · Docker Compose · GLPI · MySQL

## License
MIT

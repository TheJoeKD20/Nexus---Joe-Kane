<p align="center">
  <img src="https://nexus.joekane.org/assets/nexus-logo.png" alt="Nexus" width="92" />
</p>

<h1 align="center">Nexus</h1>

<p align="center"><b>The live support wallboard for your whole team — on every screen you own.</b></p>

<p align="center">
  <a href="https://nexus.joekane.org">Website</a> ·
  <a href="https://nexus.joekane.org/docs">Docs</a> ·
  <a href="https://nexus.joekane.org/pricing">Pricing</a> ·
  <a href="https://nexus.joekane.org/releases">Download</a> ·
  <a href="https://nexus.joekane.org/changelog">Changelog</a> ·
  <a href="https://nexus.joekane.org/security">Security</a>
</p>

<p align="center">
  <img alt="Self-hosted" src="https://img.shields.io/badge/self--hosted-your%20data%2C%20your%20server-1f6feb" />
  <img alt="Platforms" src="https://img.shields.io/badge/macOS%20·%20Windows%20·%20Linux%20·%20Docker%20·%20iOS%20·%20Android-informational" />
  <img alt="Release" src="https://img.shields.io/badge/release-v1.61.0-2ea043" />
  <img alt="Licence" src="https://img.shields.io/badge/licence-proprietary-555" />
</p>

<p align="center">
  <img src="https://nexus.joekane.org/assets/shots/hero.webp" alt="The Nexus wallboard" width="880" />
</p>

<p align="center">
  <a href="https://nexus.joekane.org">Website</a> ·
  <a href="https://nexus.joekane.org/docs">Docs</a> ·
  <a href="https://nexus.joekane.org/pricing">Pricing</a> ·
  <a href="https://nexus.joekane.org/releases">Download</a> ·
  <a href="https://nexus.joekane.org/changelog">Changelog</a> ·
  <a href="https://nexus.joekane.org/security">Security</a>
</p>

---

## What is Nexus?

Nexus turns your help desk into a **real-time wallboard** for the whole team — the kind that belongs on a TV across the office, on the desktop, or in your pocket. It reads the help desk you already run — Zendesk, Freshdesk, Freshservice, Jira Service Management or HaloPSA — and turns the numbers that matter into big, glanceable panels that update live: first response, SLAs at risk, CSAT, who's on, and what's still unassigned.

It's **self-hosted**. The server runs in *your* environment (Docker, a VPS, Plesk — wherever) and talks to your help desk from there; your customer data is processed on your own infrastructure and never sent to us. API keys are encrypted at rest (DPAPI on Windows, AES-256-GCM elsewhere), outbound requests are SSRF-guarded, and the container runs as non-root. Your data never leaves your server.

## Highlights

- 📺 **Built for the wall** — a TV-first board that fills **any** screen, portrait or ultrawide, edge to edge, with a kiosk/TV mode and per-screen rotation.
- 🔌 **Multi-provider** — Zendesk (Support + Talk), plus Freshdesk, Freshservice, Jira Service Management and HaloPSA *(beta)*. One board, whichever desk you run.
- 🧩 **Panels & KPIs you arrange** — drag, resize and theme a wall of live panels; layout presets and multiple boards.
- 🎨 **Themes & looks** — eleven themes (plus a custom palette) and five surface "looks" (Classic, Flat, Glass, Elevated, Contrast), previewed before you pick and mixable per screen or per board.
- 🖥️ **Screen Sync** — name your screens and push a board or a message to every TV at once from one place.
- 🔐 **Yours to lock down** — view passcode, scoped access links, an admin token, SSO/VPN-friendly. Read access is unauthenticated by design for trusted LANs.
- 🤖 **AI daily summary** *(optional)* — a plain-language read of the day, using your own LLM key.
- 🛰️ **Switchboard** *(closed-beta add-on)* — auto-routes unassigned tickets to the right engineer. See [the Switchboard page](https://nexus.joekane.org/switchboard).

## A look around

| | |
|---|---|
| <img src="https://nexus.joekane.org/assets/shots/board-tickets.webp" width="420" alt="Ticket panels" /> | <img src="https://nexus.joekane.org/assets/shots/board-sla.webp" width="420" alt="SLA war-room" /> |
| **Live ticket & talk panels** — first response, CSAT, unassigned, agent status. | **SLA war-room** — what's at risk, right now. |
| <img src="https://nexus.joekane.org/assets/shots/agent-drilldown.webp" width="420" alt="Agent drill-down" /> | <img src="https://nexus.joekane.org/assets/shots/tvmode.webp" width="420" alt="TV mode" /> |
| **Agent drill-down** — tap a name for the detail. | **TV mode** — rotating, room-readable slides. |

### Pick a look

<p>
  <img src="https://nexus.joekane.org/assets/shots/look-flat.webp" width="210" alt="Flat" />
  <img src="https://nexus.joekane.org/assets/shots/look-glass.webp" width="210" alt="Glass" />
  <img src="https://nexus.joekane.org/assets/shots/look-elevated.webp" width="210" alt="Elevated" />
  <img src="https://nexus.joekane.org/assets/shots/look-contrast.webp" width="210" alt="Contrast" />
</p>

### On the phone, too

<p>
  <img src="https://nexus.joekane.org/assets/shots/phone-panels.webp" width="200" alt="Nexus on mobile — panels" />
  <img src="https://nexus.joekane.org/assets/shots/phone-detail.webp" width="200" alt="Nexus on mobile — detail" />
</p>

## Runs everywhere

**macOS · Windows · Linux · Docker · iOS · Android · Zendesk Marketplace app.** Grab an installer from the [releases page](https://nexus.joekane.org/releases), or self-host with Docker:

```yaml
# docker-compose.yml
services:
  nexus:
    image: ghcr.io/thejoekd20/nexus:latest
    ports:
      - "3001:3001"
    restart: unless-stopped
    volumes:
      - "./data:/data"          # settings, encrypted secrets, layout, logo
    environment:
      # Required on Linux so stored secrets can be encrypted at rest:
      - DASHBOARD_SECRET_PASSPHRASE=change-me-and-keep-it-safe
```

```bash
docker compose up -d        # then open http://localhost:3001 and run the setup wizard
docker compose pull && docker compose up -d   # update to the latest release
```

The first launch walks you through a **setup wizard** (connect a provider, or try **demo mode** with built-in sample data — no account needed).

## Licensing, honestly

Nexus is a paid product (Starter / Pro / Enterprise). Licences verify **offline** with a bundled Ed25519 public key — the board renders with no phone-home, so an outage never bricks your screens. Subscribe through Stripe and your licence renews itself each billing period. The only telemetry is a minimal, opt-out heartbeat — licence id, version, plan, provider and an optional instance name, and nothing else — that confirms the subscription is live and lets a screen know when an update is ready. It's described in full in **Settings → Licence** and on the [security page](https://nexus.joekane.org/security).

## Switchboard — auto-routing

Where a ticket *should* go is a question Nexus can answer. **[Switchboard](https://nexus.joekane.org/switchboard)** is a private, closed-beta add-on that matches each unassigned ticket to the right engineer — by **specialism**, **who's actually free**, and **current load** — then either recommends the assignment or writes it straight back to your help desk. It's **deterministic and explainable**, stays hidden unless your licence carries the entitlement, and lives both as a console and as a live panel on the wall.

<p align="center">
  <img src="https://nexus.joekane.org/assets/shots/switchboard-panel.webp" width="760" alt="The Switchboard live-feed panel on the wallboard" />
</p>

→ **[Read about Switchboard](https://nexus.joekane.org/switchboard)** · request beta access at **joe@joekane.org**.

---

<p align="center">
  <a href="https://nexus.joekane.org">nexus.joekane.org</a> · Built by <a href="https://joekane.org">Joe Kane</a><br/>
  <sub>© 2026 Joe Kane. Nexus is a proprietary product. See the <a href="https://nexus.joekane.org/terms">terms</a>.</sub>
</p>

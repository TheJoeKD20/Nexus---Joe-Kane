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

---

## What is Nexus?

Nexus turns your help desk into a **real-time wallboard** for the whole team — the kind that belongs on a TV across the office, on the desktop, or in your pocket. It reads the help desk you already use and shows the numbers that matter — first response, CSAT, unassigned, who's online, SLA risk, call volume, on-call — refreshed live, so the room always knows where things stand.

It's **self-hosted**. The server runs in *your* environment (Docker, a VPS, Plesk — wherever) and talks to your help desk from there; your customer data is processed on your own infrastructure and is **never sent to us**. The desktop, mobile and wall-TV clients are stateless renderers pointed at your server.

## Highlights

- 📺 **Built for the wall** — a TV-first board that fills **any** screen, portrait or ultrawide, with a kiosk/TV mode and per-screen rotation.
- 🔌 **Multi-provider** — Zendesk (Support + Talk), plus Freshdesk, Freshservice, Jira Service Management and HaloPSA *(beta)*. One board, whichever desk you run.
- 🧩 **Panels & KPIs you arrange** — drag, resize and theme a wall of live panels; layout presets and multiple boards.
- 🎨 **Themes & looks** — nine themes and four surface "looks" (Flat, Glass, Elevated, Contrast), previewed before you pick.
- 🖥️ **Screen Sync** — name your screens and push a board or a message to every TV at once from one place.
- 🔐 **Yours to lock down** — view passcode, scoped access links, an admin token, SSO/VPN-friendly. Read access is unauthenticated by design for trusted LANs.
- 🤖 **AI daily summary** *(optional)* — a plain-language read of the day, using your own LLM key.
- 🛰️ **Switchboard** *(closed-beta add-on)* — auto-routes unassigned tickets to the right engineer. See [the Switchboard repo](https://nexus.joekane.org/switchboard).

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

Nexus is a paid product (Starter / Pro / Enterprise). Licences verify **offline** with a bundled Ed25519 public key — the board renders with no phone-home; a light heartbeat just confirms the subscription is still active and **fails open** so a blip never blanks your wall. Telemetry is a minimal, opt-out beacon (an opaque licence id, version, plan, which help-desk product, an optional board name) — **no customer data, ever** — and you can switch it off in **Settings → Licence**. See the [privacy](https://nexus.joekane.org/privacy) and [security](https://nexus.joekane.org/security) pages for the real mechanisms.

## Switchboard — auto-routing

Where a ticket *should* go is a question Nexus can answer. **[Switchboard](https://nexus.joekane.org/switchboard)** is a private, closed-beta add-on that matches each unassigned ticket to the right engineer — by specialism, live availability and load — and can assign it automatically under your rules.

<p align="center">
  <img src="https://nexus.joekane.org/assets/shots/switchboard-panel.webp" width="760" alt="The Switchboard live-feed panel on the wallboard" />
</p>

→ **[Read about Switchboard](https://nexus.joekane.org/switchboard)** · request beta access at **joe@joekane.org**.

---

<p align="center">
  <a href="https://nexus.joekane.org">nexus.joekane.org</a> · Built by <a href="https://joekane.org">Joe Kane</a><br/>
  <sub>© 2026 Joe Kane. Nexus is a proprietary product. See the <a href="https://nexus.joekane.org/terms">terms</a>.</sub>
</p>

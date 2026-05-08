# Cybersecurity Portfolio Site

**Static portfolio site that surfaces 12 cybersecurity lab projects as JSON-driven cards over an animated WebGL architecture background. Vanilla HTML/CSS/JS, no framework, no build step.**

This is the recruiter-facing showcase for the Brick Stack and Cloud Cells labs — see [Related projects](#related-projects).

---

## Why this exists

Recruiters don't want to read 17 separate READMEs. This site presents the security work as a single, browsable portfolio: each project is a card that links back to its full repo and writeup, with an animated architecture background to give the work some visual identity.

---

## How it works

```
data/portfolio.json   →   index.html (loads cards via fetch)   →   projects/<slug>.html (per-project detail)
                          + scripts/architecture.js (three.js architecture animation)
                          + scripts/render-projects.js (card rendering)
```

The card grid on the landing page is rendered client-side from `data/portfolio.json`. Each entry has `title`, `slug`, `description`, `category`, `summary`, `skills`, `tools`, and `results`. Click a card → land on `projects/<slug>.html`, a per-project page derived from `projects/template.html`.

The architecture animation (`scripts/architecture.js`) runs as a WebGL background layer beneath the UI.

---

## Projects featured

The site currently surfaces 12 projects across cyber, cloud, hardware, and web:

- SIEM Monitoring & Log Analysis Lab
- Vulnerability Management Lab
- Encrypted Live Security Environment
- Security Toolchain Environment
- Security Operations HUD Interface
- Cyberdeck Build
- Azure Infrastructure Security Lab
- Azure Security Hardening & Monitoring
- System Backup & Recovery Lab
- Time Sync Service (NetworkManager dispatcher)
- Security Lab Repository Management System
- Custom Premium Website Product

Source of truth is [`data/portfolio.json`](data/portfolio.json). Per-project pages live in [`projects/`](projects/).

---

## Local preview

The site is fully static — no build step required.

```bash
# Serve from the repo root with any static server
python3 -m http.server 8000
# or
npx serve .
```

Open `http://localhost:8000`.

---

## Regenerating portfolio.json

`scripts/generate-portfolio.py` walks a project source tree and produces `data/portfolio.json` from per-project metadata. To regenerate:

```bash
python3 scripts/generate-portfolio.py
```

(Adjust `PROJECT_ROOT` at the top of the script to match the local source tree.)

---

## Repository layout

| Path | Purpose |
|------|---------|
| `index.html` | Landing page (loads cards from `data/portfolio.json`) |
| `data/portfolio.json` | Project catalog (single source of truth) |
| `data/styles.css` | Global styles |
| `projects/*.html` | Per-project detail pages |
| `projects/template.html` | Template used when generating new project pages |
| `scripts/architecture.js` | WebGL architecture background |
| `scripts/render-projects.js` | Card rendering on the landing page |
| `scripts/generate-portfolio.py` | Builds `portfolio.json` from a source tree |
| `assets/` | Static images and project visuals |

---

## Related projects

This site is the index for these labs:

- [vulnerability-management-lab](https://github.com/RealPhantomLee/vulnerability-management-lab) — end-to-end VM lifecycle on VulnHub targets
- [logging-siem-wazuh](https://github.com/RealPhantomLee/logging-siem-wazuh) — Wazuh SIEM on Kali Live USB
- [toolchain-layer](https://github.com/RealPhantomLee/toolchain-layer) — security tool inventory and validation
- [interface-hud-operator-controls](https://github.com/RealPhantomLee/interface-hud-operator-controls) — operator HUD
- [cyberdeck-platform](https://github.com/RealPhantomLee/cyberdeck-platform) — Pi cyberdeck hardware
- [live-usb-encrypted-persistence](https://github.com/RealPhantomLee/live-usb-encrypted-persistence) — encrypted Kali Live USB
- [live-usb-auto-time-sync](https://github.com/RealPhantomLee/live-usb-auto-time-sync) — NetworkManager time-sync dispatcher
- [system-backup-brick12](https://github.com/RealPhantomLee/system-backup-brick12) — repeatable system-backup workflow
- [azure-fundamentals-cell](https://github.com/RealPhantomLee/azure-fundamentals-cell) — Azure foundation
- [azure-security-monitoring-lab](https://github.com/RealPhantomLee/azure-security-monitoring-lab) — Azure security hardening + monitoring

---

## Author

**RealPhantomLee Tucker** — [github.com/RealPhantomLee](https://github.com/RealPhantomLee)

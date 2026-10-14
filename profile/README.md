<img src="assets/banner-dark.png" alt="SYNC Lab" width="100%">

<div align="center">

# SYNC Lab

Production-grade FiveM resources built around clean UX, modular architecture,<br>
server authority, optional integrations, and reliable releases.

[Website](https://synclabscript.dev) &nbsp;·&nbsp; [Documentation](https://synclabscript.dev/docs) &nbsp;·&nbsp; [Store](https://synclab-script-store.tebex.store/) &nbsp;·&nbsp; [Discord](https://discord.gg/YjqfyxpVzM)

</div>

---

## Products

SYNC Lab develops free and paid FiveM resources distributed through official channels.

Each product is independently installable. There is no mandatory shared core that everything depends on.

### Paid

| Product | Links |
|---|---|
| **SYNC HUD** | [Website](https://synclabscript.dev) · [Docs](https://synclabscript.dev/docs) · [Store](https://synclab-script-store.tebex.store/) |
| **SYNC Reports** | [Website](https://synclabscript.dev) · [Docs](https://synclabscript.dev/docs) · [Store](https://synclab-script-store.tebex.store/) |
| **SYNC Chat** | [Website](https://synclabscript.dev) · [Docs](https://synclabscript.dev/docs) · [Store](https://synclab-script-store.tebex.store/) |

### Free

| Product | Links |
|---|---|
| **SYNC Notify** | [Docs](https://synclabscript.dev/docs) · [Source](https://github.com/SyncLabDev/sync_notify) · [Releases](https://github.com/SyncLabDev/sync_notify/releases) |
| **SYNC TextUI** | [Docs](https://synclabscript.dev/docs) · [Source](https://github.com/SyncLabDev/sync_textui) · [Releases](https://github.com/SyncLabDev/sync_textui/releases) |
| **SYNC Loading: HORIZON** | [Docs](https://synclabscript.dev/docs) · [Source](https://github.com/SyncLabDev/sync_loadingV1) · [Releases](https://github.com/SyncLabDev/sync_loadingV1/releases) |

---

## Engineering Principles

- **Server-authoritative** — clients submit intent; the server verifies, decides, and mutates
- **Modular architecture** — products own their configuration, validation, adapters, and diagnostics
- **Optional integrations** — third-party resources are adapters, not hard dependencies
- **Performance-conscious** — measurable idle and active budgets per resource
- **Secure network boundaries** — untrusted client data is always validated server-side
- **Event-driven systems** — state changes propagate through events, not polling
- **Versioned releases** — semantic versioning, immutable Git tags, changelog per release
- **Useful diagnostics** — compact health summary at startup, quiet when healthy, actionable on failure

---

## Supported Ecosystem

| Category | Supported |
|---|---|
| Frameworks | Qbox · QBCore · ESX · Standalone (per resource) |
| UI | React · TypeScript · FiveM NUI |
| Database | oxmysql |
| Optional integrations | ox_lib · ox_inventory · ox_target · pma-voice · and others (per resource) |

Check the [documentation](https://synclabscript.dev/docs) for exact compatibility per product.

---

## Repository Conventions

- Repository and FiveM resource names use lowercase snake_case: `sync_notify`, `sync_textui`
- Commercial product names use title case: `SYNC Notify`, `SYNC TextUI`
- Versions live in Git tags — never in repository names
- Paid source code is private by default

---

## Security

Security vulnerabilities must not be disclosed through public issues.

Report vulnerabilities privately. See the [Security Policy](https://github.com/SyncLabDev/.github/blob/main/SECURITY.md).

---

<div align="center">

**Built for FiveM. Designed for production.**

</div>

<div align="center">

# SYNC Lab

Production-grade FiveM resources built around clean UX, modular architecture,<br>
server authority, optional integrations, and reliable releases.

[Store](https://store.synclab.dev) &nbsp;·&nbsp; [Documentation](https://docs.synclab.dev) &nbsp;·&nbsp; [Support](https://discord.gg/Txj8xmCn7R)

</div>

---

## Products

SYNC Lab develops free and paid FiveM resources distributed through official channels.

Each product is independently installable. There is no mandatory shared core that everything depends on.

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

Check the individual repository or documentation for exact compatibility per product.

---

## Repository Conventions

- Repository names use lowercase kebab-case: `sync-notify`, `sync-safezones`
- FiveM resource names use underscores: `sync_notify`, `sync_safezones`
- Commercial product names use title case: `SYNC Notify`, `SYNC SafeZones`
- Versions live in Git tags — never in repository names
- Paid source code is private by default

---

## Security

Security vulnerabilities must not be disclosed through public issues.

Report vulnerabilities privately. See [SECURITY.md](../SECURITY.md).

---

<div align="center">

**Built for FiveM. Designed for production.**

</div>

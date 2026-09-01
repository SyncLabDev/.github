# SYNC Lab Security Policy

---

## Report a Vulnerability Privately

**Do not open a public GitHub issue for security vulnerabilities.**

Public disclosure before a fix is available puts every production FiveM server running a SYNC Lab resource at risk.

### How to report

**Option 1 — GitHub Private Security Advisory (preferred)**

Use GitHub's private advisory system for the affected repository:

```
https://github.com/SyncLabDev/<repository>/security/advisories/new
```

**Option 2 — Discord (private message)**

Contact the SYNC Lab team privately via the official support Discord:

```
https://discord.synclab.dev
```

Send a private message to a maintainer. Do not post vulnerability details in any public channel.

---

## What to Include in a Report

- Affected resource name and version
- Vulnerability description
- Reproduction steps
- Potential impact
- Relevant server/client console output
- Proof of concept (if available)
- Suggested mitigation (if known)

Do not include:
- Credentials or passwords belonging to other servers
- Personal data of other users
- Information beyond what is needed to reproduce the issue

---

## Supported Versions

Security fixes are applied to currently supported releases.

| Resource | Supported |
|---|---|
| Latest stable release | ✅ Yes |
| Previous minor release | ⚠️ Critical fixes only |
| Older releases | ❌ Not supported |

Update to the latest release before reporting a vulnerability that may already be resolved.

---

## What Qualifies as a Security Vulnerability

Report issues involving:

- Authentication or authorization bypass
- Permission bypass or privilege escalation
- Network event exploitation (spoofed events, forged payloads)
- Item or money duplication exploits
- Ownership bypass (vehicles, stashes, jobs, zones)
- Database manipulation through untrusted input
- SQL injection
- Remote code execution or arbitrary server-side execution
- Sensitive information disclosure (tokens, credentials, player data)
- Rate-limit or cooldown bypass enabling abuse at scale
- NUI-based authority escalation (client NUI granting server-side permissions)
- Licensing or escrow bypass

---

## FiveM Security Model

SYNC Lab follows one principle:

> **The client is untrusted.**

Clients submit intent. The server verifies, decides, and mutates state.

The following are always treated as untrusted on the server:

- Client Lua execution context
- NUI callbacks and JavaScript
- Network event payloads
- Client-reported coordinates
- Client-reported prices, amounts, or permissions
- Client-reported ownership or identity claims
- Hidden or disabled UI controls

Client-side checks exist only for user experience — they are never the security boundary.

---

## Secrets and Credentials

Never commit to any repository:

```
.env files
API keys
Discord bot tokens
Discord webhooks
Database passwords or connection strings
SSH private keys
Tebex secrets or license keys
Production credentials of any kind
```

If a secret is accidentally committed, assume it is compromised. Rotate it immediately.

Removing a secret from the latest commit is not sufficient — it may already exist in Git history and must be purged using appropriate tooling.

---

## Responsible Disclosure

We ask security researchers to:

- Allow maintainers reasonable time to investigate and patch before any public disclosure
- Avoid accessing data that does not belong to them
- Avoid disrupting production servers
- Avoid publishing exploitable reproduction details before remediation
- Provide sufficient information to reliably reproduce the issue

Security reports submitted in good faith are appreciated and handled with priority.

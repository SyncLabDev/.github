# SYNC Lab Security Policy

Security is an important part of SYNC Lab development.

If you discover a vulnerability affecting a SYNC Lab resource, report it responsibly.

---

## Do Not Open Public Security Issues

Do not publicly disclose vulnerabilities involving:

- Authentication bypass
- Authorization bypass
- Permission bypass
- Network event exploitation
- Item duplication
- Money exploits
- Database manipulation
- Administrative privilege escalation
- Remote code execution
- Sensitive information exposure
- Token or webhook exposure
- Licensing bypasses
- Other exploitable security weaknesses

Public disclosure before a fix is available may put production FiveM servers at risk.

---

## Reporting a Vulnerability

Security vulnerabilities should be reported privately through an official SYNC Lab security or support channel.

A report should include:

- Affected resource
- Resource version
- Vulnerability description
- Reproduction steps
- Potential impact
- Relevant logs
- Proof of concept when appropriate
- Suggested mitigation when available

Do not include credentials, personal data, or information belonging to other users or servers unless strictly necessary.

---

## Supported Versions

Security fixes are generally targeted at supported versions of SYNC Lab resources.

Users should verify that they are running a supported version before reporting a vulnerability that may already have been resolved.

---

## FiveM Security Model

SYNC Lab follows this principle:

> **The client is untrusted.**

Sensitive operations should be validated by the server.

Depending on the system, validation may include:

- Permissions
- Player state
- Position
- Distance
- Ownership
- Inventory
- Currency
- Job
- Entity state
- Request frequency
- Input type
- Input range
- Cooldowns

Client-side checks may improve user experience, but they must not be treated as authoritative security controls.

---

## Secrets and Credentials

Never commit:

```text
.env
API keys
Discord bot tokens
webhooks
database passwords
SSH private keys
Tebex secrets
license credentials
production credentials
```

If a secret is accidentally committed, assume it is compromised and rotate it immediately.

Removing a secret only from the latest commit is not sufficient if it already entered Git history.

---

## Responsible Disclosure

We ask security researchers to:

- Give maintainers reasonable time to investigate and fix an issue.
- Avoid accessing information that does not belong to them.
- Avoid disrupting production systems.
- Avoid publicly publishing exploitable details before remediation.
- Provide enough information to reliably reproduce the vulnerability.

Responsible security reports are appreciated.

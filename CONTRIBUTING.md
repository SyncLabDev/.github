# Contributing to SYNC Lab

Thank you for your interest in contributing to SYNC Lab.

SYNC Lab projects prioritize reliability, maintainability, security, performance, and consistent user experience.

---

## Development Principles

Contributions should aim for:

- Clear and maintainable code
- Modular architecture
- Secure server-side validation
- Minimal unnecessary resource usage
- Predictable APIs
- Good documentation
- Consistent naming
- Backwards compatibility where reasonable
- Production-ready behavior

Avoid unnecessary complexity.

---

## Branching Workflow

Recommended branches:

```text
main
develop
feature/*
fix/*
perf/*
refactor/*
```

Examples:

```text
feature/custom-notification-theme
feature/qbox-support
fix/notification-queue
fix/nui-focus
perf/client-thread-optimization
refactor/framework-adapter
```

Do not commit unfinished experimental work directly to `main`.

---

## Commit Messages

Use clear Conventional Commit-style prefixes:

```text
feat:
fix:
perf:
refactor:
docs:
style:
test:
build:
ci:
chore:
```

Examples:

```text
feat: add configurable notification positions
fix: release NUI focus when menu closes
perf: remove unnecessary client polling
refactor: move framework detection into bridge
docs: add qbox installation instructions
```

---

## Lua Guidelines

Lua code should be:

- Modular
- Readable
- Properly scoped
- Event-driven where possible
- Secure
- Configuration-driven where appropriate

Avoid:

- Unnecessary `while true` loops
- Permanent `Wait(0)` loops without justification
- Excessive polling
- Global variables without reason
- Duplicate framework logic
- Large monolithic files
- Client-trusted sensitive operations

---

## FiveM Security

The core security principle is:

> **Never trust the client.**

Sensitive operations must be validated on the server.

Examples include:

- Money changes
- Inventory changes
- Item rewards
- Job permissions
- Administrative actions
- Vehicle ownership
- Database mutations
- Player permissions
- Progress or reward completion
- Protected interactions

Validate where appropriate:

- Player identity
- Permissions
- Input types
- Input ranges
- Entity ownership
- Distance
- Player state
- Job state
- Resource state
- Cooldowns
- Rate limits

Never assume an event is safe because the normal UI only sends valid data.

---

## Network Events

Network events must be reviewed for abuse possibilities.

Server handlers should validate sensitive input before acting on it.

Avoid accepting client-provided:

- Prices
- Reward amounts
- Permission levels
- Arbitrary item names
- Arbitrary player IDs
- Arbitrary database values

unless the server independently validates them.

---

## NUI Development

SYNC Lab NUI projects generally use:

- React
- TypeScript
- Vite

NUI contributions should prioritize:

- FiveM CEF compatibility
- Low runtime overhead
- Correct NUI focus handling
- Responsive layouts
- Accessible interactions
- Predictable state management
- Restrained animations
- Clean component architecture
- Minimal unnecessary re-renders
- Minimal unnecessary dependencies

Avoid excessive visual effects that reduce readability or CEF performance.

Always verify that NUI focus is properly released when the interface closes.

---

## Framework Compatibility

Framework-specific logic should be isolated where practical.

Preferred architecture:

```text
bridge/
├── qbox/
├── qbcore/
├── esx/
└── standalone/
```

Avoid spreading framework detection throughout unrelated files.

Keep core business logic framework-independent where reasonably practical.

---

## Pull Requests

Every pull request should explain:

- What changed
- Why it changed
- How it was tested
- Performance impact
- Security implications
- Breaking changes

Visual changes should include screenshots or videos where useful.

---

## Bug Reports

Before submitting a bug report:

1. Update to a supported version.
2. Read available documentation.
3. Search existing issues.
4. Reproduce the problem.
5. Check the client console.
6. Check the server console.
7. Collect relevant logs.

Never publish:

- Passwords
- API keys
- Tokens
- Discord webhooks
- Database credentials
- License keys
- Private server credentials

---

## Code Review

A contribution may be rejected if it:

- Introduces a security risk
- Causes unnecessary performance degradation
- Breaks compatibility without justification
- Duplicates existing functionality
- Adds unnecessary dependencies
- Does not follow project architecture
- Is insufficiently tested
- Contains debug-only code
- Reduces maintainability

---

## Licensing

By contributing code to an open-source SYNC Lab repository, you agree that your contribution may be distributed under that repository's existing license.

Commercial or private SYNC Lab repositories may use separate contribution and licensing requirements.

# Contributing to SYNC Lab

SYNC Lab projects prioritize security, performance, reliability, and maintainable architecture.
Contributions should reflect those values.

---

## Engineering Philosophy

### Independent resources

Each SYNC product is independently installable. Do not architect contributions around a mandatory shared core.

Every product owns:
- its configuration and validation
- its adapter contracts
- its diagnostics
- its locale handling
- its failure handling

### Adapter contracts over direct calls

Business logic must not call optional third-party resources directly.

```
SYNC business logic
        ↓
Capability contract  (e.g. SYNC.Inventory)
        ↓
Integration resolver
        ↓
Adapter
        ↓
Third-party resource
```

Never scatter direct calls to `ox_inventory`, `ox_target`, or similar resources throughout gameplay code.

### Fail gracefully

Optional integration failures must not crash or disable unrelated functionality.

---

## Branching

```
main          — production
feature/*     — new functionality
fix/*         — bug fixes
refactor/*    — code restructuring
perf/*        — performance work
docs/*        — documentation only
security/*    — security fixes
```

**Do not use permanent branches** such as `dev`, `develop`, `staging`, `beta`, or `release` unless the workflow genuinely requires them.

---

## Commit Messages

Use Conventional Commits:

```
feat:
fix:
refactor:
perf:
docs:
security:
chore:
```

With optional scope:

```
feat(target): add ox_target adapter
fix(reports): prevent duplicate case claim on reconnect
perf(safezones): reduce idle proximity check interval
security(employment): validate ownership server-side before mutation
docs(notify): document locale override system
refactor(framework): isolate detection into bridge module
```

Keep commit messages factual. No `fix`, `oops`, `maybe fixed`, `real final`.

---

## Merge Policy

Use **squash and merge** for feature and fix branches.

Main branch history must remain readable. Do not preserve intermediate work-in-progress commits.

---

## Lua Guidelines

```lua
-- Preferred
RegisterNetEvent('sync_resource:server:action', function(payload)
    local src = source
    -- validate every field before use
    -- never trust client-provided state, ownership, or permission claims
end)
```

Avoid:
- Permanent `Wait(0)` threads outside frame-sensitive operations
- Polling when events would suffice
- Global variables without explicit reason
- Framework detection outside the bridge module
- Large monolithic files

Performance targets:

| State | Target |
|---|---|
| Fully idle | ~0.00–0.02 ms |
| Light passive monitoring | ~0.01–0.05 ms |
| Normal active | < 0.10 ms |
| Complex temporary state | < 0.20–0.30 ms |
| Persistent > 0.5 ms | Investigate |
| Persistent > 1.0 ms | Normally unacceptable |

---

## Configuration Validation

Every product validates its configuration at startup without requiring a shared core.

Validate:
- missing required settings
- invalid types
- unsupported enum values
- impossible numeric ranges
- malformed integration values
- unsupported framework values
- deprecated settings

Errors must be actionable:

```
[SYNC Resource] Configuration validation failed

Setting:  Config.Framework
Value:    qbx
Expected: qbox | qbcore | esx | standalone

Action:   Change Config.Framework to a supported value.
```

Do not emit a bare `attempt to index nil` and leave users to guess the cause.

---

## Diagnostics

Separate audit logging from developer debugging.

Default startup output must be a compact health summary:

```
SYNC Resource 1.0.0

Config        OK
Database      OK
Framework     Qbox
Integrations  3 ready
Locale        en

Ready
```

Do not spam individual loading lines unless `Config.Debug` granular categories are enabled.

Support per-category debug flags. Do not create a single global debug toggle that floods every subsystem.

---

## Locale Standard

English (`locales/en.lua`) is mandatory and canonical.

Resolution order:
1. Custom override
2. Selected locale
3. English fallback
4. `[missing.key]` — never a crash

Use stable dot-notation keys:

```
reports.create.title
reports.errors.cooldown
staff.case.assigned
```

Use named placeholders:

```lua
Welcome %{player}   -- preferred
Welcome %s          -- avoid
```

Missing translation keys must never crash gameplay.

---

## Security

### Core principle

> **Never trust the client.**

Clients submit intent. The server verifies, decides, and mutates.

Treat as untrusted on the server:
- client Lua execution
- NUI callbacks and JavaScript
- network event payloads
- client-reported coordinates, prices, amounts, permissions, IDs, ownership

### Every sensitive network event must validate

```lua
-- Bad
RegisterNetEvent('sync_resource:claimReward', function(rewardId, amount)
    -- using client-provided amount directly
    GiveItem(source, 'cash', amount)
end)

-- Good
RegisterNetEvent('sync_resource:claimReward', function(rewardId)
    local src = source
    local reward = Config.Rewards[rewardId]
    if not reward then return end
    if not HasPermission(src, 'claim') then return end
    if IsOnCooldown(src, 'claimReward') then return end
    GiveItem(src, reward.item, reward.amount)
end)
```

Validate for every exposed event:
- type, length, range, enum, table size, nested depth, allowed values

Use parameterized queries. Never concatenate untrusted values into SQL.

### Rate limits and cooldowns

- **Rate limit** — protects infrastructure from abuse
- **Cooldown** — enforces gameplay rules

Do not ban immediately on a single rate-limit hit. Reject → count → aggregate → enforce based on policy.

### Distance validation

Physical interactions validate server-side distance using trusted config coordinates.

```lua
-- Client sends intent
TriggerServerEvent('sync_resource:useShop', shopId)

-- Server resolves trusted coordinates from config — never from client
local shop = Config.Shops[shopId]
if not shop then return end
local playerCoords = GetEntityCoords(GetPlayerPed(source))
if #(playerCoords - shop.coords) > shop.radius then return end
```

### NUI security

NUI is never authoritative. Ignore authority fields sent by NUI:

```
isAdmin, owner, price, allowed, grade
```

Server derives those independently from trusted state.

---

## Framework Compatibility

Isolate framework-specific logic in a bridge directory:

```
integrations/
├── framework/
│   ├── qbox.lua
│   ├── qbcore.lua
│   ├── esx.lua
│   └── standalone.lua
```

Keep core business logic framework-independent.

---

## Optional Integration Policy

Optional integrations use `auto | none | <explicit> | custom` configuration.

Auto-detection must:
1. Inspect supported resources
2. Resolve by documented priority
3. Detect and warn on ambiguity
4. Load only the selected adapter
5. Report useful diagnostics
6. Recover from dependency restart where appropriate

Do not silently pick unpredictably when multiple compatible providers exist.

---

## Pull Requests

Every PR must explain:
- What changed and why
- How it was tested (frameworks, scenarios)
- Security implications
- Performance impact
- Breaking changes
- Configuration or database changes

Visual or NUI changes require screenshots or a short video.

---

## Code Review Standards

A contribution may be rejected if it:
- Introduces a security risk
- Causes unjustified performance degradation
- Breaks compatibility without documented reason
- Adds unnecessary dependencies
- Ignores the adapter contract pattern
- Contains debug-only code
- Reduces diagnostic quality
- Does not follow project architecture

---

## Licensing

By contributing to a public SYNC Lab repository, you agree your contribution may be distributed under that repository's existing license.

Private or commercial repositories use separate contribution and licensing requirements.

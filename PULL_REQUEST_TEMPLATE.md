# Pull Request

## Summary

<!-- What does this PR do? One or two sentences. -->

## Reason

<!-- Why is this change necessary? Link the problem or issue being solved. -->

Closes #

## Changes

<!-- List the specific changes made. Be precise. -->

-
-

---

## Testing

<!-- How was this tested? List the exact steps a reviewer can follow to verify the change. -->

Framework tested:

- [ ] Qbox
- [ ] QBCore
- [ ] ESX
- [ ] Standalone
- [ ] Not applicable

---

## Screenshots / NUI Changes

<!-- Include screenshots or a short video for any UI or NUI change. -->

---

## Impact Review

### Security

- [ ] Client-provided data is treated as untrusted
- [ ] Sensitive actions are validated server-side
- [ ] Network events were reviewed for abuse potential
- [ ] Permission checks cover all affected paths
- [ ] Input types, ranges, and lengths are validated
- [ ] No credentials, tokens, webhooks, or API keys are included

Security notes:

### Performance

```
Client idle:
Client active:
Server impact:
NUI impact:
```

Performance notes:

### Configuration

- [ ] No configuration change
- [ ] New optional setting added (with sensible default)
- [ ] Existing setting changed (backward compatible)
- [ ] Breaking configuration change — documented below

Configuration notes:

### Database

- [ ] No database change
- [ ] Migration included
- [ ] Migration is backward compatible
- [ ] Breaking migration — documented below

Database notes:

---

## Breaking Changes

<!-- Does this change break anything for users on the current version? -->

- [ ] No breaking changes
- [ ] Breaking change — describe what users must update:

---

## Documentation

- [ ] No documentation update required
- [ ] README updated
- [ ] CHANGELOG updated
- [ ] Inline comments updated
- [ ] External docs updated

---

## Final Checklist

- [ ] Self-review completed — I read every changed line
- [ ] Relevant tests pass
- [ ] Security impact reviewed
- [ ] Performance impact reviewed
- [ ] No debug code or debug logs left in
- [ ] No secrets or credentials included
- [ ] Configuration compatibility reviewed
- [ ] Database migration reviewed
- [ ] Documentation updated where required
- [ ] CHANGELOG updated where required
- [ ] Breaking changes identified and documented
- [ ] All review conversation threads resolved

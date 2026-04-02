[← Previous](./01-intro.md) | [📋 Index](./README.md) | [Next →](./02-1-commit-basics.md)

---

# Branch Structure

## Three Permanent Branches

| Branch | Purpose | Deploy Target |
|--------|---------|---------------|
| `main` | Production releases | Production |
| `stage` | QA validation | Staging |
| `dev` | Feature integration | Dev/Integration |

**All are protected — no direct pushes!**

---

## Branch Lifecycle

```
feature/JIRA-123 ──PR──► dev ──PR──► stage ──PR──► main
     │                                               │
     └── created from dev                    tagged: v1.2.0
```

---

## Temporary Branch Types

| Type | Created From | Merges To | When to Use |
|------|--------------|-----------|-------------|
| `feature/*` | `dev` | `dev` | New functionality |
| `fix/*` | `dev` | `dev` | Non-urgent QA bug |
| `bugfix/*` | `stage` | `stage` | Urgent staging fix |
| `hotfix/*` | `main` | `main` | Production emergency |


---

[← Previous](./01-intro.md) | [📋 Index](./README.md) | [Next →](./02-1-commit-basics.md)

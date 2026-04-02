[← Previous](./11-cicd-pipeline.md) | [📋 Index](./README.md) | [Next →](./13-releases.md)

---

# Branch Protection Rules

## Protection Settings

| Rule | `dev` | `stage` | `main` |
|------|-------|---------|--------|
| Direct push | Blocked | Blocked | Blocked |
| Force push | Blocked | Blocked | Blocked |
| Pipeline must pass | Yes | Yes | Yes |
| Min approvals | 1 | 2 | 2 + Tech Lead |

**No exceptions — pipeline must pass before merge!**


---

[← Previous](./11-cicd-pipeline.md) | [📋 Index](./README.md) | [Next →](./13-releases.md)

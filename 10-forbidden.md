[← Previous](./09-2-rebase-danger.md) | [📋 Index](./README.md) | [Next →](./11-cicd-pipeline.md)

---

# What's Forbidden

## NEVER Do This on dev, stage, or main

```bash
git rebase <anything>
git push --force
git push --force-with-lease
git reset --hard
git commit --amend && push -f
```

**These rewrite shared history and break everyone's work!**

---

## Collaborative Features

When multiple devs work on one feature:

```
feature/AUTH-100              ← shared parent
  ├── feature/AUTH-100-backend   ← dev A
  └── feature/AUTH-100-frontend  ← dev B
```

Sub-branches **merge** to parent (not rebase!)
Use merge in both directions — parent is shared.


---

[← Previous](./09-2-rebase-danger.md) | [📋 Index](./README.md) | [Next →](./12-branch-protection)

[← Previous](./05-push-and-cleanup.md) | [📋 Index](./README.md) | [Next →](./07-bugfix-urgent.md)

---

# Bug Fixes Decision Tree

## Bug Found During QA?

```
Is staging broken or release blocked?
│
├── NO  → fix/* from dev (normal flow)
│         Promoted with next dev → stage cycle
│
└── YES → bugfix/* from stage (expedited)
          ↳ Fast-tracked: skips dev→stage flow
          Mandatory backport to dev within 24h
```

---

## Fix Branch (Non-Urgent)

**Same flow as feature branch:**

```bash
git checkout dev && git pull origin dev
git checkout -b fix/QA-300-wrong-calculation
git commit -m "fix(cart): correct tax rounding"
git fetch origin dev && git rebase origin/dev
git push -u origin fix/QA-300-wrong-calculation
```

PR/MR → `dev` → promoted to stage in next cycle


---

[← Previous](./05-push-and-cleanup.md) | [📋 Index](./README.md) | [Next →](./07-bugfix-urgent.md)

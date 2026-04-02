[← Previous](./07-bugfix-urgent.md) | [📋 Index](./README.md) | [Next →](./09-1-merge-strategy.md)

---

# Hotfix (Production Emergency)

## Hotfix Branch

```bash
# Create from MAIN
git checkout main && git pull origin main
git checkout -b hotfix/PROD-99-fix-description

# Apply minimal fix only — no refactoring
git commit -m "fix(payment): prevent null pointer"
git push -u origin hotfix/PROD-99-fix-description
```

MR/PR → `main` (1 tech lead approval)

---

## Double Backport (Both mandatory within 24h!)

```bash
# Backport to dev
git checkout dev && git pull origin dev
git checkout -b backport/PROD-99-to-dev
git cherry-pick <hotfix-merge-sha>  # copies commit to dev
git push -u origin backport/PROD-99-to-dev

# Backport to stage
git checkout stage && git pull origin stage
git checkout -b backport/PROD-99-to-stage
git cherry-pick <hotfix-merge-sha>  # copies commit to stage
git push -u origin backport/PROD-99-to-stage
```


---

[← Previous](./07-bugfix-urgent.md) | [📋 Index](./README.md) | [Next →](./09-1-merge-strategy.md)

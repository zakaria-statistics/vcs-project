[← Previous](./06-bug-decision-tree.md) | [📋 Index](./README.md) | [Next →](./08-hotfix.md)

---

# Bugfix (Urgent)

## Bugfix Branch — When Staging is Broken

```bash
# Create from STAGE
git checkout stage && git pull origin stage
git checkout -b bugfix/QA-400-checkout-crash

# Minimal fix only — no refactoring, just fix the issue
git commit -m "fix(checkout): handle empty cart"
git push -u origin bugfix/QA-400-checkout-crash
```

MR/PR → `stage` (expedited: 1 approval instead of 2)

---

## Mandatory Backport (within 24 hours!)

```bash
git checkout dev && git pull origin dev
git checkout -b backport/QA-400-to-dev
git cherry-pick <bugfix-merge-commit-sha>  # copies this single commit
git push -u origin backport/QA-400-to-dev
```

MR/PR → `dev`


---

[← Previous](./06-bug-decision-tree.md) | [📋 Index](./README.md) | [Next →](./08-hotfix.md)

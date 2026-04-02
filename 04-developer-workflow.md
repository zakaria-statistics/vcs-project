[← Previous](./03-naming-conventions.md) | [📋 Index](./README.md) | [Next →](./05-push-and-cleanup.md)

---

# Developer Workflow

## Step 1: Start Fresh

```bash
git checkout dev
git pull origin dev
git checkout -b feature/JIRA-123-description
```

---

## Step 2: Make Commits

```bash
git add .
git commit -m "feat(payment): add Stripe integration"
```

**Use Conventional Commits:**
- `feat:` — new feature
- `fix:` — bug fix
- `test:` — tests
- `docs:` — documentation
- `refactor:` — code restructure

---

## Step 3: Stay Current (MANDATORY)

```bash
git fetch origin dev
git rebase origin/dev
```

**Do this daily, before MR, and before pushing!**


---

[← Previous](./03-naming-conventions.md) | [📋 Index](./README.md) | [Next →](./05-push-and-cleanup.md)

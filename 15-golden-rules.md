[← Previous](./14-2-performance-practices.md) | [📋 Index](./README.md) | Next →

---

# Golden Rules & Quick Reference

## The 10 Golden Rules

1. **Never push directly** to protected branches
2. **Always rebase** your feature branch on dev before MR
3. **Never rebase** shared branches
4. **Backport** all bugfixes and hotfixes
5. **Use conventional commits**
6. **Minimal fixes only** for bugfix/hotfix — reduces deployment risk
7. **Tag releases** immediately after stage → main merge
8. **Delete feature branches** after merge
9. **Pipeline must pass** before merge
10. **Get required approvals** — no bypassing!

---

## Quick Reference: Daily Commands

```bash
# Start feature
git checkout dev && git pull  # fetch + merge remote changes
git checkout -b feature/JIRA-123-desc

# Stay current
git fetch origin dev && git rebase origin/dev

# Push
git push -u origin feature/JIRA-123-desc
git push --force-with-lease  # safe force push — fails if someone else pushed first
```

---

## Quick Reference: Promotions

```bash
# Check what will be promoted
git log origin/stage..origin/dev --oneline

# Tag release after merge to main
git tag -a v1.2.0 -m "Release v1.2.0"
git push origin v1.2.0
```

---


## Questions?

---

## Thank You!

**Remember:**
- Protect shared branches
- Rebase locally, merge shared
- Always backport
- Pipeline is your friend

---

[← Previous](./14-2-performance-practices.md) | [📋 Index](./README.md) | Next →

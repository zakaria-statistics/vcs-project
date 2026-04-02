[← Previous](./12-branch-protection.md) | [📋 Index](./README.md) | [Next →](./14-conventions.md)

---

# Releases & Tagging

## Semantic Versioning

```
v<MAJOR>.<MINOR>.<PATCH>

v1.0.0    ← production release
v1.1.0    ← new feature
v1.1.1    ← hotfix
v2.0.0    ← breaking change
```

---

## Creating a Release

```bash
git checkout main && git pull origin main
git tag -a v1.2.0 -m "Release v1.2.0: payment gateway"
git push origin v1.2.0
```

Release pipeline auto-deploys!

**Tag immediately after stage → main merge.**


---

[← Previous](./12-branch-protection.md) | [📋 Index](./README.md) | [Next →](./14-conventions.md)

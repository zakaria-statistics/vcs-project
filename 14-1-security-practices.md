[← Previous](./14-conventions.md) | [📋 Index](./README.md) | [Next →](./14-2-performance-practices.md)

---

# Security Best Practices

## Never Commit Secrets!

**These should NEVER be in your repo:**
- API keys, tokens, passwords
- `.env` files with credentials
- Private keys (SSH, GPG, SSL certificates)
- Database connection strings
- Cloud credentials (AWS, GCP, Azure)

---

## Essential .gitignore for Security

```gitignore
# Environment files
.env
.env.local
.env.*.local
*.env

# Credentials & Keys
*.pem
*.key
*.p12
*.pfx
credentials.json
secrets.yaml

# IDE with potential secrets
.idea/
.vscode/settings.json
```

---

## Pre-Commit Hooks (Recommended)

Use tools to catch secrets BEFORE they're committed:

```bash
# Install pre-commit
pip install pre-commit

# Add to .pre-commit-config.yaml
repos:
  - repo: https://github.com/gitleaks/gitleaks
    rev: v8.18.0
    hooks:
      - id: gitleaks
```

---

## ⚠️ Accidentally Committed a Secret?

**STOP! The secret is already exposed.** Even if you delete it, it's in Git history.

**Immediate actions:**
1. **Rotate the secret immediately** — generate new API key/password
2. **Revoke the old secret** — disable it in the service
3. Remove from history (if needed):
   ```bash
   git filter-branch --force --index-filter \
     "git rm --cached --ignore-unmatch path/to/secret" \
     --prune-empty --tag-name-filter cat -- --all
   ```
4. **Force push** (coordinate with team!)
5. **Notify security team**

**Remember:** Rotation is MORE important than removing from history!


---

[← Previous](./14-conventions.md) | [📋 Index](./README.md) | [Next →](./14-2-performance-practices.md)

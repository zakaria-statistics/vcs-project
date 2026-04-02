[← Previous](./14-1-security-practices.md) | [📋 Index](./README.md) | [Next →](./15-golden-rules.md)

---

# Performance Best Practices

## Don't Commit These Files!

**Generated/Reproducible files:**
```gitignore
# Dependencies
node_modules/
vendor/
.venv/
__pycache__/

# Build outputs
dist/
build/
*.min.js
*.min.css
*.bundle.js

# IDE & OS
.idea/
.vscode/
.DS_Store
Thumbs.db

# Logs & temp
*.log
*.tmp
*.cache
```

---

## Git LFS for Large Files

**Use Git LFS for binary files > 100KB:**
- Images, videos, audio
- PDFs, Office documents
- Compiled binaries, archives
- Design files (PSD, Sketch, Figma exports)

```bash
# Install & setup
git lfs install

# Track file types
git lfs track "*.psd"
git lfs track "*.zip"
git lfs track "*.mp4"

# Commit .gitattributes
git add .gitattributes
git commit -m "chore: configure Git LFS"
```

---

## Keep Commits Small & Focused

**Good practices:**
- One logical change per commit
- Commit often, push regularly
- Don't mix refactoring with features

**Bad:**
```bash
git commit -m "Add login, fix bugs, refactor utils, update deps"
```

**Good:**
```bash
git commit -m "feat(auth): add login form"
git commit -m "fix(auth): handle empty password"
git commit -m "refactor(utils): extract validation helpers"
```

---

## Repo Hygiene Checklist

| Practice | Why |
|----------|-----|
| Use `.gitignore` | Prevent bloat from generated files |
| Use Git LFS | Large binaries slow down clone/fetch |
| Small commits | Easier review, bisect, revert |
| Delete merged branches | Keep repo clean |
| Prune stale remotes | `git remote prune origin` |
| Regular `git gc` | Optimize local repo |

---

## CI/CD Performance Tips

```yaml
# Shallow clone (faster checkout)
variables:
  GIT_DEPTH: 10

# Cache dependencies
cache:
  paths:
    - node_modules/
    - .npm/
```


---

[← Previous](./14-1-security-practices.md) | [📋 Index](./README.md) | [Next →](./15-golden-rules.md)

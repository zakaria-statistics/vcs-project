[← Previous](./02-branch-structure.md) | [📋 Index](./README.md) | [Next →](./02-2-git-workspaces.md)

---

# Git Commit Basics

## What is a Commit?

A **commit** is not just code changes — it's a **history node** with links:

```
commit [a1b2c3d...]  ← SHA (unique hash ID)
├── tree      → snapshot of files
├── parent    → pointer to previous commit(s)
├── author    → who wrote the change
├── committer → who applied the commit
└── message   → "fix login bug"
```

---

## SHA (Commit ID)

Each commit has a unique **SHA** — a hash of its entire content.

```
a1b2c3d4e5f6...
```

**If anything changes, the SHA changes:**
- different message → different SHA
- different parent → different SHA
- different author date → different SHA

---

## Parent & Child

Git history is a **linked graph**:

```
A ← B ← C
```

- `B` has `A` as **parent** (stored in commit)
- `B` is **child** of `A` (inferred by Git)

---

## Pointers (Branches, Tags, HEAD)

A **pointer** is a reference to a commit:

```
A ← B ← C ← D
            ↑
          main (branch pointer)
            ↑
          HEAD (current position)
```

When you commit, the branch pointer moves forward.

---

## Why This Matters for Rebase

Because **parent SHA is part of the commit**:

```
parent changes → SHA changes → NEW commit
```

Rebase changes the parent → all commits get **rewritten with new SHAs**.

This breaks other developers' work based on old commits!

---

## Quick Glossary

| Term | Meaning |
|------|---------|
| **commit** | Snapshot + history node |
| **SHA** | Unique hash ID of commit |
| **parent** | Previous commit link |
| **child** | Later commit referencing this as parent |
| **pointer** | Branch/tag/HEAD reference to a commit |
| **author** | Who originally wrote the change |
| **committer** | Who applied/committed it |


---

[← Previous](./02-branch-structure.md) | [📋 Index](./README.md) | [Next →](./02-2-git-workspaces.md)

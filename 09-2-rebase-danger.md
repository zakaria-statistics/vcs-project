[← Previous](./09-1-merge-strategy.md) | [📋 Index](./README.md) | [Next →](./10-forbidden.md)

---

# Why Never Rebase Shared Branches?

**Rebase rewrites commit history** — creates NEW commits with different SHAs.

**Scenario:** Dev A and Dev B working on collaborative feature:
```
feature/AUTH-100              ← shared parent
  ├── feature/AUTH-100-backend   ← Dev A
  └── feature/AUTH-100-frontend  ← Dev B
```

```
BEFORE:                       AFTER Dev A rebases parent on dev:

feature/AUTH-100              feature/AUTH-100
    │                             │
    ├── X ← Y ← Z                 ├── X' ← Y' ← Z' (new SHAs!)
    │                             │
Dev B's branch                Dev B's branch
    └── based on Z                └── based on OLD Z (orphaned!)
```

**What happens to Dev B's work:**
- Dev B's commits are based on commit `Z`
- Dev A rebases parent → `Z` becomes `Z'` (different SHA)
- Dev B's branch now points to a commit that **no longer exists** in parent
- Dev B's work becomes **orphaned** — disconnected, effectively lost

---

## Orphaned Commits Visualized

```
BEFORE REBASE:

dev:
[c1]───[c2]───[c3]
        │
        └───┐
            │
            ▼
feature/AUTH-100 (parent):      branched from c2
[c1]───[c2]───[p1]───[p2]───[p3]
                              │
                              └───┐
                                  │
                                  ▼
feature/AUTH-100-frontend:        branched from p3
[c1]───[c2]───[p1]───[p2]───[p3]───[b1]───[b2]



AFTER DEV A REBASES feature/AUTH-100 ON dev:

dev (unchanged):
[c1]───[c2]───[c3]


feature/AUTH-100 (parent) - REBASED ON dev:
[c1]───[c2]───[c3]───[p1']───[p2']───[p3']  ◄── feature/AUTH-100 points HERE now
                      │       │       │
                     NEW     NEW     NEW
                     SHA     SHA     SHA


┌─────────────────────────────────────────────────────────────────────────┐
│  ⚠️  ORPHANED ZONE — DETACHED FROM PARENT                               │
│                                                                         │
│                                                                         │
│         [p1]───[p2]───[p3]  ✗ ─ ─ ─ ─ ─ ┐                               │
│                        │                ┊ DETACHED!                     │
│                        │                ┊ parent pointer moved to p3'   │
│                        ▼                ┊                               │
│                  [b1]───[b2]  ◄── feature/AUTH-100-frontend             │
│                                                                         │
│                                                                         │
│   Dev B's branch based on p3, but p3 is no longer in parent history!   │
│   These commits are now ORPHANED — floating without connection.         │
└─────────────────────────────────────────────────────────────────────────┘
```

**When Dev B tries to merge/push:**
- Git sees divergent histories (`p3` vs `p3'`)
- Results in merge conflicts or duplicate commits
- Dev B may have to **redo all their work**

---

## What Makes a Branch "Shared"?

A branch is **shared** if:
- Other developers have based their work on it
- It's been pushed and others have pulled/fetched it
- It's a protected branch (`dev`, `stage`, `main`)
- It's a collaborative feature branch with multiple contributors

**Rule:** If in doubt, use merge. Orphaned commits = lost work.


---

[← Previous](./09-1-merge-strategy.md) | [📋 Index](./README.md) | [Next →](./10-forbidden.md)

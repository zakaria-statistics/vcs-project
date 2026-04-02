[← Previous](./04-developer-workflow.md) | [📋 Index](./README.md) | [Next →](./06-bug-decision-tree.md)

---

# Push & Cleanup

## Step 4: Push & Create MR

```bash
# First push
git push -u origin feature/JIRA-123-description

# After rebase (only YOUR branch)
git push --force-with-lease origin feature/JIRA-123-description
```

> **--force-with-lease:** Safe force push — fails if someone else pushed first.

Then create MR: `feature/JIRA-123` → `dev`

> **MR (Merge Request):** GitLab's pull request — a formal request to merge your branch into another.

---

## Step 5: Cleanup

```bash
git checkout dev
git pull origin dev
git branch -d feature/JIRA-123-description
```

Remote branch is auto-deleted by GitLab.


---

[← Previous](./04-developer-workflow.md) | [📋 Index](./README.md) | [Next →](./06-bug-decision-tree.md)

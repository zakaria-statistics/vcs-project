[← Previous](./10-forbidden.md) | [📋 Index](./README.md) | [Next →](./12-branch-protection.md)

---

# CI/CD Pipeline

## Pipeline Stages

### Feature → Dev
```
Build → Lint → Unit Tests → SAST → Secrets → Light E2E
```

### Dev → Stage
```
Full Integration → API Contract → DB Migration → E2E → Perf
```

### Stage → Main
```
Manual Approval → Full E2E → Security Audit → Deploy
```

---

## Pipeline Failures

| Failed Job | Action |
|------------|--------|
| `build` | Fix syntax/deps, run locally |
| `lint` | Run `npm run lint:fix` |
| `unit_tests` | Fix test or implementation |
| `sast` | Review finding, fix code |
| `secret_detection` | **Remove secret, rotate key!** |


---

[← Previous](./10-forbidden.md) | [📋 Index](./README.md) | [Next →](./12-branch-protection.md)

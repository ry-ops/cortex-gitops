# Cortex GitOps

**The source of truth for all Cortex k3s deployments.**

## The Control Plane Whispers; The Cluster Thunders

This repository contains all Kubernetes manifests for the Cortex platform. ArgoCD watches this repository and automatically syncs changes to the k3s cluster.

## Structure

```
cortex-gitops/
├── apps/                       # Application manifests organized by namespace
│   ├── cortex-system/         # Core platform services
│   ├── cortex/                # Main cortex services
│   ├── cortex-chat/           # Chat interface
│   ├── cortex-cicd/           # CI/CD pipelines
│   ├── cortex-dev/            # Development tools
│   ├── cortex-security/       # Security services
│   ├── cortex-knowledge/      # Knowledge management
│   └── cortex-autonomous/     # Autonomous agents
├── argocd-apps/               # ArgoCD Application definitions
├── base/                      # Base manifests and kustomizations
└── README.md
```

## Workflow

1. **Update manifests** in this repository
2. **Commit and push** to main branch
3. **ArgoCD detects changes** and syncs to cluster
4. **Cluster pulls and deploys** automatically

## Rules

- ✅ All cluster resources MUST be defined here
- ✅ Changes go through Git (version control + audit trail)
- ✅ ArgoCD enforces self-healing (manual kubectl changes are reverted)
- ❌ No direct kubectl apply (except emergencies with audit log)

## Emergency Procedures

If ArgoCD is down or broken:

1. Apply fix: `kubectl apply -f emergency-fix.yaml`
2. Log it: `echo "[date] EMERGENCY: reason" >> ~/cortex-audit.log`
3. Commit to GitOps: Copy fix to this repo and commit immediately
4. Verify ArgoCD syncs after recovery

---

**Version**: 1.0.0
**Last Updated**: 2026-01-11
**Directive**: CLAUDE.md v2.1.0 (Project Thunder)

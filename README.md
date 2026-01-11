# Cortex GitOps Repository

GitOps repository for Cortex infrastructure deployments via ArgoCD.

## Structure

- `csaf/` - Cortex Security App Framework manifests
- `tui/` - Cortex TUI (Terminal User Interface) manifests
- `control-plane/` - Control Plane architecture manifests
- `apps/` - ArgoCD Application definitions

## Deployment

All deployments are managed by ArgoCD running in the k3s cluster.

```bash
# Add this repository to ArgoCD
argocd repo add https://github.com/ry-ops/cortex-gitops.git

# Applications will auto-sync to the cluster
```

## Projects

### CSAF (Cortex Security App Framework)
Natural language to security monitoring apps pipeline.

### Cortex TUI
Real-time terminal dashboard for k3s cluster monitoring.

### Control Plane
GitOps enforcement architecture with ArgoCD.

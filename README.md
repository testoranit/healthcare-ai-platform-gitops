# Healthcare AI Platform GitOps

Kubernetes desired state for the Healthcare AI RAG Platform.

The app pipeline updates the dev overlay image tag after a successful image build, scan, push, and signature.

## Layout

- `apps/healthcare-ai-agent/base`: shared Kubernetes manifests
- `apps/healthcare-ai-agent/overlays/dev`: dev image/env settings
- `apps/healthcare-ai-agent/overlays/stage`: stage promotion target
- `apps/healthcare-ai-agent/overlays/prod`: prod promotion target
- `platform/argocd`: ArgoCD Application definitions

## Manual render check

```powershell
kubectl kustomize apps/healthcare-ai-agent/overlays/dev
```

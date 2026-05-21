# Step 5 GitOps Setup

Push this folder to:

```text
testoranit/healthcare-ai-platform-gitops
```

The app pipeline updates:

```text
apps/healthcare-ai-agent/overlays/dev/kustomization.yaml
```

ArgoCD later reads the manifests from:

```text
platform/argocd/app-healthcare-ai-agent-dev.yaml
platform/argocd/app-healthcare-ai-agent-stage.yaml
platform/argocd/app-healthcare-ai-agent-prod.yaml
```

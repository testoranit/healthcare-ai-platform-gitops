# Step 6 Kubernetes Security and Operations

## What was added

- Namespace security labels for `dev`, `stage`, and `prod`
- Kyverno installation through ArgoCD
- Kyverno policies for Healthcare AI namespaces only
- kube-prometheus-stack installation through ArgoCD
- Topology spread and writable `/tmp` volume for the read-only app container

## Apply order

Apply ArgoCD apps in this order:

```powershell
kubectl apply -f platform/argocd/app-kyverno.yaml
kubectl apply -f platform/argocd/app-kyverno-policies.yaml
kubectl apply -f platform/argocd/app-monitoring.yaml
kubectl apply -f platform/argocd/app-healthcare-ai-agent-dev.yaml
```

## Verify

```powershell
kubectl get pods -n kyverno
kubectl get clusterpolicy
kubectl get pods -n monitoring
kubectl get pods -n healthcare-ai-dev
kubectl get hpa,pdb,networkpolicy -n healthcare-ai-dev
```

## Notes

- Policies match only namespaces labeled `app.kubernetes.io/part-of=healthcare-ai-platform`.
- The app remains in `APP_MODE=mock` until the Bedrock Knowledge Base and Guardrail IDs are available.
- Replace the Grafana admin password with a secret-backed value before treating this as real production.

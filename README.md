# ArgoCD Configuration

### Setup ArgoCD

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

### ArogCD Admin Password

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

### Generate SSH Keys

```
ssh-keygen -t ed25519 -C "subhadeep762@gmail.com" -f .ssh/argocd_ed25519
or
ssh-keygen -t rsa -b 4096 -C "subhadeep762@gmail.com" -f .ssh/argocd_rsa
```

### Encode SSH to Base64

```
cat argo | base64 -w 0
```

## Install Cert-Manager

```
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.12.0/cert-manager.yaml
```

## Change Service Type

```
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
```

## Visualize service

```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
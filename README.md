# ArgoCD Configuration

### To Run ArgoCD
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
ssh-keygen -f argo
```

### Encode SSH to Base64
```
cat argo | base64 -w 0
```

## Install Cert-Manager
```
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.12.0/cert-manager.yaml
```
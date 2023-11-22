## check agocd admin password
```
kubectl -n argocd get secret argocd-initial-admin-secret -ojsonpath={.data.password} | base64 -d
```
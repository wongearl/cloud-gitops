## check agocd admin password
```
kubectl -n argocd get secret argocd-initial-admin-secret -ojsonpath={.data.password} | base64 -d
```
## 关联gitlab

### create SSH Key Pair
```
ssh-keygen -o -t rsa -b 4096 -C "940200885@qq.com"
```
### copy id_rsa.pub to gitlab

### copy id_rsa to gitlab secret-repo-lgp.yaml sshPrivateKey
## install kubeseal
```
KUBESEAL_VERSION='0.23.0'
wget "https://github.com/bitnami-labs/sealed-secrets/releases/download/v${KUBESEAL_VERSION:?}/kubeseal-${KUBESEAL_VERSION:?}-linux-amd64.tar.gz"
tar -xvzf kubeseal-${KUBESEAL_VERSION:?}-linux-amd64.tar.gz kubeseal
sudo install -m 755 kubeseal /usr/local/bin/kubeseal
```
## create secret
```
kubectl -n argocd create secret generic argo-workflows-sso --dry-run=client --from-literal=client-id=8923959489517ab7909d18f79bf0e62cb7c270403101ba5821d9da3c6fb6b042 --from-literal=client-secret=8c03e5c00f45932555be5e9cf618ca0ce0b994666a85971b1bdaf44fa216f23d -o yaml | \
    kubeseal \
      --controller-name=sealed-secrets-controller \
      --controller-namespace=kube-system \
      --format yaml > mysealedsecret.yaml

kubectl apply -f mysealedsecret.yaml -n argocd
```

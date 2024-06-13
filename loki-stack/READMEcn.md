# Loki-Stack Helm Chart

```bash
helm -n logging install loki ./loki-stack/
kubectl patch svc loki-grafana -n logging -p '{"spec": {"type": "NodePort"}}'
kubectl get secret --namespace logging loki-grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
````
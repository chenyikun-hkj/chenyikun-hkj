# kube

## kubectl
- Query the config by a host
```bash
kubectl get ingress -n services -o json | jq '.items | .[].spec.rules | select(.[].host=="api.test2.testhireez.com")' | jq -s 'map(.[]) | .[].http.paths' | jq -s 'map(.[])' | jq 'map({ type:.pathType, path:.path, service:.backend.service.name})'
```
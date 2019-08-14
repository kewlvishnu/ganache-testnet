Run the following commands:

This will deploy Traefik:
```helm install --name traefik-ingress --namespace kube-system --set dashboard.enabled=true,dashboard.domain=dashboard.infernos.io,rbac.enabled=true stable/traefik```

This will deploy ganachecli (This must be run from the root of the git repo):
```helm install ./charts --name my-release2 --namespace kube-system```

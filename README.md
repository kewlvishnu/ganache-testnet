Run the following commands:

This will deploy Traefik:
```helm install --name traefik-ingress --namespace kube-system --set dashboard.enabled=true,dashboard.domain=dashboard.infernos.io,rbac.enabled=true stable/traefik```

This will deploy ganachecli (This must be run from the root of the git repo):
```helm install ./charts --name testnet1 --namespace default```

NOTE: Traefik and testnet dont have to be in the name namespace.

Helm chart repo location: https://infernos-chart.storage.googleapis.com/ganache-testnet-1.0.0.tgz

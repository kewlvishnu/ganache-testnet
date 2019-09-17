Run the following commands:

This will deploy Traefik:
```helm install --name traefik-ingress --namespace kube-system --set dashboard.enabled=true,dashboard.domain=dashboard.infernos.io,rbac.enabled=true stable/traefik```

create secret: https://docs.traefik.io/user-guide/kubernetes/#creating-the-secret

 ```htpasswd -c ./auth myusername```
 
 ```cat auth``` 
 
 ```kubectl create secret generic mysecret --from-file auth --namespace=default```

Then enable basic auth: https://docs.traefik.io/v1.5/configuration/backends/kubernetes/#authentication
NOTE: The chart by default uses the kubernetes secret: `mysecret`. To change it change the value in the Values,yaml file. 

Additions support docs: https://stackoverflow.com/questions/50130797/kubernetes-basic-authentication-with-traefik


This will deploy ganachecli (This must be run from the root of the git repo):
```helm install ./charts --name testnet1 --namespace default```



NOTE: Traefik and testnet dont have to be in the name namespace.

Helm chart repo location: https://infernos-chart.storage.googleapis.com/ganache-testnet-1.0.0.tgz
How to publish Helm Charts: https://helm.sh/docs/developing_charts/#prerequisites-1

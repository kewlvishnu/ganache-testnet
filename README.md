Run the following commands:

This will deploy Traefik:
```helm install --name traefik-ingress --namespace kube-system --set dashboard.enabled=true,dashboard.domain=dashboard.infernos.io,rbac.enabled=true,externalTrafficPolicy=Local stable/traefik```

create secret: https://docs.traefik.io/user-guide/kubernetes/#creating-the-secret

 ```htpasswd -c ./auth myusername```
 
 ```cat auth``` 
 
 ```kubectl create secret generic mysecret --from-file auth --namespace=default```

Then enable basic auth: https://docs.traefik.io/v1.5/configuration/backends/kubernetes/#authentication
NOTE: The chart by default uses the kubernetes secret: `mysecret`. To change it change the value in the Values,yaml file. 

Additions support docs: https://stackoverflow.com/questions/50130797/kubernetes-basic-authentication-with-traefik


This will deploy ganachecli (This must be run from the root of the git repo):
```helm install ./charts --name testnet1 --namespace default  --set ganachecli.whitelistIP="173.48.233.154/32\,0.0.0.0/0"```



NOTE: Traefik and testnet dont have to be in the name namespace.

Helm chart repo location: https://infernos-chart.storage.googleapis.com/ganache-testnet-1.0.0.tgz

How to publish Helm Charts: https://helm.sh/docs/developing_charts/#prerequisites-1

  001  "Update the index.yaml with the latest version -- vi ganache-testnet/index.yaml"  
  002  helm package ganache-testnet  
  003  ls  
  004  mkdir chart-repo  
  005  mv ganache-testnet-latest-version.tgz chart-repo/  
  006  helm repo index chart-repo --url https://infernos-chart.storage.googleapis.com  
  007  cd chart-repo/  
  008  ls  
  009  cat index.yaml   
  010  cd ..  
  011  mv ganache-testnet-1.0.0.tgz chart-repo/  
  012  mv test-chart-0.1.0.tgz chart-repo/ .    ---- this step is done to make sure all the charts are present in the folder  
  013  helm repo index chart-repo --url https://infernos-chart.storage.googleapis.com  
  014  cd chart-repo/  
  015  ls  
  016  cat index.yaml   -- varify all the charts are listed in the index.yaml in the folder chart-repo  
  017  cd ..  
  018  gsutil cp chart-repo/* gs://infernos-chart 

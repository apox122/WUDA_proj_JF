## Local environment

Requirements:
1. Kubectl
```
winget install -e --id Kubernetes.kubectl
```
2. Helm
```
winget install Helm.Helm
```
3. Kubernetes.Kind
```
winget install Kubernetes.kind
```


### Kind
**Remember to launch docker engine first.**</br> 
Delete old cluster
```
kind delete cluster
```

Create cluster:
```
cd .\boardgames
kind create cluster --config kind-config.yaml
```
Install NGINX 
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
```

## IMPORTANT set up dns for remote access on the cluster
1. Run notepad as administrator
2. Open C:\Windows\System32\drivers\etc\hosts
3. Add in etc/hosts 
```
127.0.0.1 boardgames.local
```

### Helm
Run following to deploy to the cluster for the first time:

Create the dedicated namespace:
```
kubectl create namespace klawon-frydrych
```
then

```
helm install <release-name> boardgames/ --values boardgames/values.yaml
```
Example
```
 helm install testjf boardgames/ --values boardgames/values.yaml -n klawon-frydrych
```

Then for every update:
```
helm upgrade <release-name> boardgames/ --values boardgames/values.yaml
```
Example
```
helm upgrade testjf boardgames/ --values boardgames/values.yaml -n klawon-frydrych
```
Set specific value from values in terminal (i.e. disable db deployment):
```
helm upgrade boardgames/ --values boardgames/values.yaml --set postgres.enabled=false
```
### APP 
Application is available on address
```
http://boardgames.local
```

### Kubectl
To see pods:
```
kubectl get pods -n klawon-frydrych --watch
```

To see pods + more information:
```
kubectl get all
```


## Kubernetes cluster

### Kubeconfig

To use kubekonfig file, download it and place anywhere on the drive. Then, copy path and run following command in terminal:

```
set KUBECONFIG=<PATH>
```




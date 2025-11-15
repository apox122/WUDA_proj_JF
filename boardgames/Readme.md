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
Create cluster:
```
kind create cluster
```

### Helm
Run following to deploy to the cluster for the first time:
```
helm install <release-name> boardgames/ --values boardgames/values.yaml
```

Then for every update:
```
helm upgrade <release-name> boardgames/ --values boardgames/values.yaml
```

Set specific value from values in terminal (i.e. disable db deployment):
```
helm upgrade boardgames/ --values boardgames/values.yaml --set postgres.enabled=false
```

### Kubectl
To see pods:
```
kubectl get pods
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




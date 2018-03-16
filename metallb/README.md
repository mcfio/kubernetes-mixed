# MetalLB

Deployment is pulled directly from MetalLB's installation guide
```
kubectl apply -f https://raw.githubusercontent.com/google/metallb/v0.4.5/manifests/metallb.yaml
```

Customized the configmap, MetalLB has a config watcher and automatically reloads
```
kubectl apply -f metallb-configmap.yaml
```

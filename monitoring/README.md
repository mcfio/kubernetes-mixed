# Monitoring Setup

Create the namespace
```
kubectl create namespace "monitoring"
```

Create prometheus operator in the "monitoring" namespace
```
kubectl -n monitoring apply -f prometheus-operator
```

Create necessary exporters in the "monitoring" namespace
```
kubectl -n monitoring apply -f node-exporter
kubectl -n monitoring apply -f kube-state-metrics
```

Create grafana instance in the "monitoring" namespace
```
kubectl -n monitoring apply -f grafana/grafana-credentials.yaml
kubectl -n monitoring apply -f grafana
```

Create prometheus service in the "monitoring" namespace
```
kubectl -n monitoring apply -f prometheus/prometheus-k8s-rules.yaml
kubectl -n monitoring apply -f prometheus/prometheus-k8s.yaml
kubectl -n monitoring apply -f prometheus/prometheus-k8s-service.yaml
```

Add prometheus roles and role bindings necessary for prometheus to monitor across the ClusterRole
```
kubectl apply -f prometheus/prometheus-k8s-roles.yaml
kubectl apply -f prometheus/prometheus-k8s-role-bindings.yaml
```

Add alertmanager in the monitirong namespaces
```
kubectl -n monitoring apply -f alertmanager
```

Create the service monitors for services we want to monitor
```
kubectl -n monitoring apply -f service_monitors
```

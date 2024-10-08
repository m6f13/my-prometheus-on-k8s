# Prometheus / Grafana on Kubernetes

## add REPOS / HELM
```shell
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add stable https://charts.helm.sh/stable
helm repo update
```

## pull chart from repo and untar chart locally
```shell
cd repo/helm
helm pull prometheus-community/kube-prometheus-stack --untar
```

## install chart from local directory
```shell
kubectl create ns monitoring
helm upgrade --install prom01 ./charts/kube-prometheus-stack -f ./charts/kube-prometheus-stack/values.yaml -n monitoring
```

## access Grafana
```shell
kubectl -n monitoring port-forward service/prom01-grafana 3000
```

## Grafana user: admin / default password: prom-operator

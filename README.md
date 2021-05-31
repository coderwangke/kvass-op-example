# kvass-op-example

#### 1. 创建 `namespace: monitoring`
```
$ kubectl create ns monitoring
```

#### 2. 通过 helm 部署 prometheus-operator
```
$ helm repo add stable https://charts.helm.sh/stable

$ helm upgrade --install prom-op stable/prometheus-operator --namespace monitoring -f values.yaml
```

#### 3. 部署 kvass 组件 coordinator 

```
# 先创建rbac权限
$ kubectl apply -f ./kvass-rbac.yaml

$ kubeclt apply -f ./coordiantor.yaml
```

#### 4. 部署 prometheus

```
$ kubectl apply -f ./prometheus-rep-0.yaml
```

#### 5. 部署 thanos 组件

```
$ kubectl apply -f thanos-query.yaml

$ kubectl apply -f thanos-rule.yaml
```

#### 6. 部署测试服务

```
$ kubectl apply -f metrics.yaml

$ kubectl apply -f service-monitor.yaml
```
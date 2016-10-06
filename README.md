# Playing with Kubernetes in minikube

Sets up a local Kubernetes v1.4 cluster with graphs enabled.

## Steps

Start the local cluster

```
minikube start --vm-driver=xhyve --kubernetes-version=v1.4.0
```

Deploy and run UI

```
minikube dashboard
```

Bootstrap some stuff

```
kubectl create -f kube-system
```

Deploy prometheus

```
kubectl create -f monitoring
```

Deploy a sample app

```
kubectl create -f nginx
```

Run load test

```
echo "GET http://192.168.64.14:30001/" | vegeta attack -duration 60s -rate 500 | vegeta report
```

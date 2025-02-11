# Deploy minikube

```
$ sudo apt update
$ sudo apt install -y curl wget apt-transport-https
$ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
$ sudo install minikube-linux-amd64 /usr/local/bin/minikube
$ minikube version
```
It sets up your kubectl to point to it automagically:
```
$ kubectl version -o yaml
$ minikube start --driver=docker
$ kubectl cluster-info
$ minikube status
$ kubectl get nodes
```

# k8s-primer

## Prerequisites
1. Install [minikube](https://minikube.sigs.k8s.io/docs/start/) and [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)
2. Clone the repo
```
$ git clone git@github.com:jamesma100/k8s-primer.git
$ cd k8s-primer/
```
Make sure you can see your image by running `docker images`.

## Setup
1. Start up minikube
```
$ minikube start
```
2. Build local Docker image
```
$ cd app/
$ docker build -t simpleflask .
```
3. Point your shell to minikube's Docker daemon:
```
$ eval $(minikube -p minikube docker-env)
```
This is important! Otherwise minikube will pull images from its own Docker registry instead of your local.

4. Create a deployment

```
$ cd manifests/
$ kubectl create -f helloworld.yml
```
Verify your deployment exists and that 3 pods are running
```
$ kubectl get deployments
NAME          READY   UP-TO-DATE   AVAILABLE   AGE
hello-world   3/3     3            3           6s

$ kubectl get pods
NAME                           READY   STATUS    RESTARTS   AGE
hello-world-6ffb67d86d-4nkdb   1/1     Running   0          72s
hello-world-6ffb67d86d-8s6hj   1/1     Running   0          72s
hello-world-6ffb67d86d-stzlp   1/1     Running   0          72s
```

5. Stop your cluster
```
$ minikube stop
```

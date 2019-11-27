# Local Docker Cluster Bring-Up

## Prereqs

- Install minikube, Virtualbox and kubectl.

- Your favorite editor.


## Install Minikube

Download and install minikube:


Mac OS X
```
brew install minikube
```

Linux 
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_1.5.2.deb \
 && sudo dpkg -i minikube_1.5.2.deb
```

Hypervisor Setup
Verify that your system has virtualization support enabled:

```
egrep -q 'vmx|svm' /proc/cpuinfo && echo yes || echo no
```

Windows:

Download and run the minikube installer: https://storage.googleapis.com/minikube/releases/latest/minikube-installer.exe


## Check minikube ip
```
$ minikube ip
192.168.99.109 
```

put your minikube ip into no_proxy settings in .bash_profile

## Setup Kubectl

Download `kubectl` to your local directory, and add your local
directory to your path:

Mac OS X
```
curl -O http://storage.googleapis.com/kubernetes-release/release/v1.16.0/bin/darwin/amd64/kubectl
chmod 755 kubectl
PATH=$PATH:$(pwd)
```

Linux
```
wget http://storage.googleapis.com/kubernetes-release/release/v1.16.0/bin/linux/amd64/kubectl
chmod 755 kubectl
PATH=$PATH:$(pwd)
```

Windows (with bash)
```
wget https://storage.googleapis.com/kubernetes-release/release/v1.16.0/bin/windows/amd64/kubectl.exe
chmod 755 kubectl
PATH=$PATH:$(pwd)
```

##Kubectl cheatsheet (usefull during the workshop)

https://kubernetes.io/docs/reference/kubectl/cheatsheet/


##Known issue Mac OS X

```
docker pull kubeimage/kube-addon-manager:v9.0.2
```

```
docker save k8s.gcr.io/kube-addon-manager | ssh -o UserKnownHostsFile=/dev/null \
    -o StrictHostKeyChecking=no -o LogLevel=quiet \
    -i ~/.minikube/machines/minikube/id_rsa docker@$(minikube ip) docker load
```

In another terminal, create an ssh tunnel for kubectl to talk to your cluster. Leave this running.

```
docker-machine ssh $(docker-machine active) -N -L 8080:localhost:8080
```


## Check that your cluster is running

```
kubectl get nodes

```
```
NAME       STATUS   ROLES    AGE   VERSION
minikube   Ready    master   12d   v1.16.2
```
## Check services

```
kubectl get po -A
```
```
NAMESPACE              NAME                                         READY   STATUS             RESTARTS   AGE
kube-system            coredns-5644d7b6d9-tlhm2                     1/1     Running            1          12d
kube-system            coredns-5644d7b6d9-v9wdn                     1/1     Running            1          12d
kube-system            etcd-minikube                                1/1     Running            1          12d
kube-system            kube-addon-manager-minikube                  1/1     Running            1          12d
kube-system            kube-apiserver-minikube                      1/1     Running            1          12d
kube-system            kube-controller-manager-minikube             1/1     Running            1          12d
kube-system            kube-proxy-zfdz6                             1/1     Running            1          12d
kube-system            kube-scheduler-minikube                      1/1     Running            1          12d
kube-system            storage-provisioner                          1/1     Running            2          12d
```

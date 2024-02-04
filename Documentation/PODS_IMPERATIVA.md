# Criando PODS de forma imperativa (CLI)

## Verificando status do minikube
Comando: **minikube status**

Saída:
```bash
minikube
type: Control Plane
host: Stopped
kubelet: Stopped
apiserver: Stopped
kubeconfig: Stopped
```

## Iniciando o minikube
Comando: **minikube start**

Saída:
```bash
* minikube v1.26.0 on Debian 11.1 (vbox/amd64)
* Using the docker driver based on existing profile
* Starting control plane node minikube in cluster minikube
* Pulling base image ...
* Restarting existing docker container for "minikube" ...
! This container is having trouble accessing https://k8s.gcr.io
* To pull new external images, you may need to configure a proxy: https://minikube.sigs.k8s.io/docs/reference/networking/proxy/
* Preparing Kubernetes v1.24.1 on Docker 20.10.17 ...
* Verifying Kubernetes components...
  - Using image gcr.io/k8s-minikube/storage-provisioner:v5
* Enabled addons: storage-provisioner, default-storageclass
* Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
```

## Verificando status do minikube iniciado
Comando: **minikube start**

Saída:
```bash
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```

## Listando todos os PODS
Comando: **kubectl get --all-namespaces**

Saída:
```bash
NAMESPACE     NAME                               READY   STATUS    RESTARTS        AGE
kube-system   coredns-6d4b75cb6d-9klkc           1/1     Running   5 (9m53s ago)   20h
kube-system   etcd-minikube                      1/1     Running   5 (9m58s ago)   20h
kube-system   kube-apiserver-minikube            1/1     Running   5 (9m57s ago)   20h
kube-system   kube-controller-manager-minikube   1/1     Running   5 (9m58s ago)   20h
kube-system   kube-proxy-mbrwz                   1/1     Running   5 (9m58s ago)   20h
kube-system   kube-scheduler-minikube            1/1     Running   5 (9m48s ago)   20h
kube-system   storage-provisioner                1/1     Running   9 (2m54s ago)   20h
```

## Listando PODS criado pelo Desenvolvedor/DevOps quando não foi criado
Comando: **kubectl get pods**

Saída:
```bash
No resources found in default namespace.
```

## Criando um POD
Comando: **kubectl run my-pod-apache-server --image httpd**

Saída:
```bash
pod/my-pod-apache-server created
```

## Listando um POD criado pelo Desenvolvedor/DevOps
Comando: **kubectl get pods -o wide**

Saída:
```bash
NAME                   READY   STATUS             RESTARTS   AGE   IP           NODE       NOMINATED NODE   READINESS GATES
my-pod-apache-server   0/1     ImagePullBackOff   0          40s   172.17.0.3   minikube   <none>           <none>
```

## Listando todos os PODS
Comando: **kubectl get pods --all-namespaces**

Saída:
```bash
NAMESPACE     NAME                               READY   STATUS         RESTARTS      AGE
default       my-pod-apache-server               0/1     ErrImagePull   0             89s
kube-system   coredns-6d4b75cb6d-9klkc           1/1     Running        5 (17m ago)   20h
kube-system   etcd-minikube                      1/1     Running        5 (17m ago)   20h
kube-system   kube-apiserver-minikube            1/1     Running        5 (17m ago)   20h
kube-system   kube-controller-manager-minikube   1/1     Running        5 (17m ago)   20h
kube-system   kube-proxy-mbrwz                   1/1     Running        5 (17m ago)   20h
kube-system   kube-scheduler-minikube            1/1     Running        5 (17m ago)   20h
kube-system   storage-provisioner                1/1     Running        9 (10m ago)   20h
```

## Deletando um POD
Comando: **kubectl delete pods my-pod-apache-server**

Saída:
```bash
pod "my-pod-apache-server" deleted
```

## Criando multiplos PODS
Comando: **kubectl run my-pod-n**

Saída:
```bash
pod/my-pod-n created
```

## Deletando todos os PODS
Comando: **kubectl delete --all pods**

Saída:
```bash
pod "my-pod-2" deleted
pod "my-pod-3" deleted
```

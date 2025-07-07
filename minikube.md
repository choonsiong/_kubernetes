# Minikube

- Setup minikube
    - Install kubectl
        - [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
    - Install minikube
        - [minikube start](https://minikube.sigs.k8s.io/docs/start/?arch=%2Fmacos%2Fx86-64%2Fstable%2Fbinary+download)

### Install `kubectl`

```
tecnomen@debian12:~$ curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/arm64/kubectl"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   138  100   138    0     0    529      0 --:--:-- --:--:-- --:--:--   530
100 55.0M  100 55.0M    0     0  26.7M      0  0:00:02  0:00:02 --:--:-- 38.5M
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/arm64/kubectl.sha256"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   138  100   138    0     0    505      0 --:--:-- --:--:-- --:--:--   507
100    64  100    64    0     0    157      0 --:--:-- --:--:-- --:--:--  1361
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
kubectl: OK
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
[sudo] password for tecnomen: 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ kubectl version --client
Client Version: v1.33.2
Kustomize Version: v5.6.0
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ kubectl version --client --output=yaml
clientVersion:
  buildDate: "2025-06-17T18:41:31Z"
  compiler: gc
  gitCommit: a57b6f7709f6c2722b92f07b8b4c48210a51fc40
  gitTreeState: clean
  gitVersion: v1.33.2
  goVersion: go1.24.4
  major: "1"
  minor: "33"
  platform: linux/arm64
kustomizeVersion: v5.6.0

tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
```
# Minikube

- Setup minikube
    - Install kubectl
        - [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
    - Install minikube
        - [minikube start](https://minikube.sigs.k8s.io/docs/start/?arch=%2Fmacos%2Fx86-64%2Fstable%2Fbinary+download)

### Install Docker

Refer [this guide](https://docs.docker.com/engine/install/debian/) for installing Docker on Debian.

First, uninstall all conflicting packages

```
tecnomen@debian12:~$ for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
[sudo] password for tecnomen: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'docker.io' is not installed, so not removed
The following package was automatically installed and is no longer required:
  linux-image-6.1.0-32-arm64
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 122 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'docker-doc' is not installed, so not removed
The following package was automatically installed and is no longer required:
  linux-image-6.1.0-32-arm64
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 122 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'docker-compose' is not installed, so not removed
The following package was automatically installed and is no longer required:
  linux-image-6.1.0-32-arm64
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 122 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'podman-docker' is not installed, so not removed
The following package was automatically installed and is no longer required:
  linux-image-6.1.0-32-arm64
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 122 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'containerd' is not installed, so not removed
The following package was automatically installed and is no longer required:
  linux-image-6.1.0-32-arm64
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 122 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'runc' is not installed, so not removed
The following package was automatically installed and is no longer required:
  linux-image-6.1.0-32-arm64
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 122 not upgraded.
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
```

Then install Docker

```
tecnomen@debian12:~$ 
tecnomen@debian12:~$ sudo apt-get update
Get:1 http://security.debian.org/debian-security bookworm-security InRelease [48.0 kB]
Get:2 http://security.debian.org/debian-security bookworm-security/main Sources [142 kB]
Get:3 http://security.debian.org/debian-security bookworm-security/main arm64 Packages [268 kB]
Hit:4 https://ftp.lanet.kr/debian bookworm InRelease                       
Get:5 https://ftp.lanet.kr/debian bookworm-updates InRelease [55.4 kB]
Fetched 513 kB in 1s (349 kB/s)     
Reading package lists... Done
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ sudo apt-get install ca-certificates curl
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
curl is already the newest version (7.88.1-10+deb12u12).
The following package was automatically installed and is no longer required:
  linux-image-6.1.0-32-arm64
Use 'sudo apt autoremove' to remove it.
The following packages will be upgraded:
  ca-certificates
1 upgraded, 0 newly installed, 0 to remove and 121 not upgraded.
Need to get 0 B/155 kB of archives.
After this operation, 3072 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Reading changelogs... Done
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LC_CTYPE = "UTF-8",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to a fallback locale ("en_US.UTF-8").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Preconfiguring packages ...
(Reading database ... 204885 files and directories currently installed.)
Preparing to unpack .../ca-certificates_20230311+deb12u1_all.deb ...
Unpacking ca-certificates (20230311+deb12u1) over (20230311) ...
Setting up ca-certificates (20230311+deb12u1) ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Updating certificates in /etc/ssl/certs...
rehash: warning: skipping ca-certificates.crt,it does not contain exactly one certificate or CRL
2 added, 0 removed; done.
Processing triggers for man-db (2.11.2-2) ...
Processing triggers for ca-certificates (20230311+deb12u1) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...
done.
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ sudo install -m 0755 -d /etc/apt/keyrings
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ sudo chmod a+r /etc/apt/keyrings/docker.asc
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ sudo apt-get update
Get:1 https://download.docker.com/linux/debian bookworm InRelease [47.0 kB]
Hit:2 http://security.debian.org/debian-security bookworm-security InRelease                            
Get:3 https://download.docker.com/linux/debian bookworm/stable arm64 Packages [43.3 kB]
Hit:4 https://ftp.lanet.kr/debian bookworm InRelease                             
Hit:5 https://ftp.lanet.kr/debian bookworm-updates InRelease
Fetched 90.3 kB in 1s (113 kB/s)
Reading package lists... Done
tecnomen@debian12:~$ 
tecnomen@debian12:~$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-image-6.1.0-32-arm64
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  docker-ce-rootless-extras iptables libip6tc2 libslirp0 pigz slirp4netns
Suggested packages:
  cgroupfs-mount | cgroup-lite docker-model-plugin firewalld
The following NEW packages will be installed:
  containerd.io docker-buildx-plugin docker-ce docker-ce-cli docker-ce-rootless-extras docker-compose-plugin iptables libip6tc2 libslirp0 pigz slirp4netns
0 upgraded, 11 newly installed, 0 to remove and 121 not upgraded.
Need to get 86.9 MB of archives.
After this operation, 401 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 https://download.docker.com/linux/debian bookworm/stable arm64 containerd.io arm64 1.7.27-1 [22.8 MB]
Get:7 https://download.docker.com/linux/debian bookworm/stable arm64 docker-ce-cli arm64 5:28.3.1-1~debian.12~bookworm [14.9 MB]
Get:2 https://ftp.lanet.kr/debian bookworm/main arm64 libip6tc2 arm64 1.8.9-2 [18.7 kB]
Get:8 https://download.docker.com/linux/debian bookworm/stable arm64 docker-ce arm64 5:28.3.1-1~debian.12~bookworm [17.0 MB]
Get:9 https://download.docker.com/linux/debian bookworm/stable arm64 docker-buildx-plugin arm64 0.25.0-1~debian.12~bookworm [13.6 MB]
Get:3 https://ftp.lanet.kr/debian bookworm/main arm64 iptables arm64 1.8.9-2 [352 kB]
Get:10 https://download.docker.com/linux/debian bookworm/stable arm64 docker-ce-rootless-extras arm64 5:28.3.1-1~debian.12~bookworm [5819 kB]
Get:11 https://download.docker.com/linux/debian bookworm/stable arm64 docker-compose-plugin arm64 2.38.1-1~debian.12~bookworm [12.2 MB]
Get:4 https://ftp.lanet.kr/debian bookworm/main arm64 pigz arm64 2.6-1 [56.2 kB]
Get:5 https://ftp.lanet.kr/debian bookworm/main arm64 libslirp0 arm64 4.7.0-1 [58.4 kB]
Get:6 https://ftp.lanet.kr/debian bookworm/main arm64 slirp4netns arm64 1.2.0-1 [36.6 kB]
Fetched 86.9 MB in 2s (39.4 MB/s)                                                 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LC_CTYPE = "UTF-8",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to a fallback locale ("en_US.UTF-8").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously unselected package containerd.io.
(Reading database ... 204887 files and directories currently installed.)
Preparing to unpack .../00-containerd.io_1.7.27-1_arm64.deb ...
Unpacking containerd.io (1.7.27-1) ...
Selecting previously unselected package docker-ce-cli.
Preparing to unpack .../01-docker-ce-cli_5%3a28.3.1-1~debian.12~bookworm_arm64.deb ...
Unpacking docker-ce-cli (5:28.3.1-1~debian.12~bookworm) ...
Selecting previously unselected package libip6tc2:arm64.
Preparing to unpack .../02-libip6tc2_1.8.9-2_arm64.deb ...
Unpacking libip6tc2:arm64 (1.8.9-2) ...
Selecting previously unselected package iptables.
Preparing to unpack .../03-iptables_1.8.9-2_arm64.deb ...
Unpacking iptables (1.8.9-2) ...
Selecting previously unselected package docker-ce.
Preparing to unpack .../04-docker-ce_5%3a28.3.1-1~debian.12~bookworm_arm64.deb ...
Unpacking docker-ce (5:28.3.1-1~debian.12~bookworm) ...
Selecting previously unselected package pigz.
Preparing to unpack .../05-pigz_2.6-1_arm64.deb ...
Unpacking pigz (2.6-1) ...
Selecting previously unselected package docker-buildx-plugin.
Preparing to unpack .../06-docker-buildx-plugin_0.25.0-1~debian.12~bookworm_arm64.deb ...
Unpacking docker-buildx-plugin (0.25.0-1~debian.12~bookworm) ...
Selecting previously unselected package docker-ce-rootless-extras.
Preparing to unpack .../07-docker-ce-rootless-extras_5%3a28.3.1-1~debian.12~bookworm_arm64.deb ...
Unpacking docker-ce-rootless-extras (5:28.3.1-1~debian.12~bookworm) ...
Selecting previously unselected package docker-compose-plugin.
Preparing to unpack .../08-docker-compose-plugin_2.38.1-1~debian.12~bookworm_arm64.deb ...
Unpacking docker-compose-plugin (2.38.1-1~debian.12~bookworm) ...
Selecting previously unselected package libslirp0:arm64.
Preparing to unpack .../09-libslirp0_4.7.0-1_arm64.deb ...
Unpacking libslirp0:arm64 (4.7.0-1) ...
Selecting previously unselected package slirp4netns.
Preparing to unpack .../10-slirp4netns_1.2.0-1_arm64.deb ...
Unpacking slirp4netns (1.2.0-1) ...
Setting up libip6tc2:arm64 (1.8.9-2) ...
Setting up docker-buildx-plugin (0.25.0-1~debian.12~bookworm) ...
Setting up containerd.io (1.7.27-1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /lib/systemd/system/containerd.service.
Setting up docker-compose-plugin (2.38.1-1~debian.12~bookworm) ...
Setting up docker-ce-cli (5:28.3.1-1~debian.12~bookworm) ...
Setting up libslirp0:arm64 (4.7.0-1) ...
Setting up pigz (2.6-1) ...
Setting up docker-ce-rootless-extras (5:28.3.1-1~debian.12~bookworm) ...
Setting up slirp4netns (1.2.0-1) ...
Setting up iptables (1.8.9-2) ...
update-alternatives: using /usr/sbin/iptables-legacy to provide /usr/sbin/iptables (iptables) in auto mode
update-alternatives: using /usr/sbin/ip6tables-legacy to provide /usr/sbin/ip6tables (ip6tables) in auto mode
update-alternatives: using /usr/sbin/iptables-nft to provide /usr/sbin/iptables (iptables) in auto mode
update-alternatives: using /usr/sbin/ip6tables-nft to provide /usr/sbin/ip6tables (ip6tables) in auto mode
update-alternatives: using /usr/sbin/arptables-nft to provide /usr/sbin/arptables (arptables) in auto mode
update-alternatives: using /usr/sbin/ebtables-nft to provide /usr/sbin/ebtables (ebtables) in auto mode
Setting up docker-ce (5:28.3.1-1~debian.12~bookworm) ...
Created symlink /etc/systemd/system/multi-user.target.wants/docker.service → /lib/systemd/system/docker.service.
Created symlink /etc/systemd/system/sockets.target.wants/docker.socket → /lib/systemd/system/docker.socket.
Processing triggers for man-db (2.11.2-2) ...
Processing triggers for libc-bin (2.36-9+deb12u10) ...
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ sudo docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
c9c5fd25a1bd: Pull complete 
Digest: sha256:940c619fbd418f9b2b1b63e25d8861f9cc1b46e3fc8b018ccfe8b78f19b8cc4f
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (arm64v8)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

tecnomen@debian12:~$ 
tecnomen@debian12:~$ docker ps
permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.51/containers/json": dial unix /var/run/docker.sock: connect: permission denied
tecnomen@debian12:~$ sudo docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
tecnomen@debian12:~$ sudo docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                      PORTS     NAMES
6b30376029f3   hello-world   "/hello"   47 seconds ago   Exited (0) 46 seconds ago             inspiring_dijkstra
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 

tecnomen@debian12:~$ sudo usermod -aG docker $USER && newgrp docker
... loading /etc/bash.bashrc
... loading .bashrc
tecnomen@debian12:~$ 
```

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

### Install minikube

```
tecnomen@debian12:~$ curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-arm64
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100  122M  100  122M    0     0   225k      0  0:09:16  0:09:16 --:--:--  185k
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ sudo install minikube-linux-arm64 /usr/local/bin/minikube && rm minikube-linux-arm64
[sudo] password for tecnomen: 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ minikube start
😄  minikube v1.36.0 on Debian 12.10 (arm64)
👎  Unable to pick a default driver. Here is what was considered, in preference order:
    ▪ docker: Not healthy: "docker version --format {{.Server.Os}}-{{.Server.Version}}:{{.Server.Platform.Name}}" exit status 1: permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.51/version": dial unix /var/run/docker.sock: connect: permission denied
    ▪ docker: Suggestion: Add your user to the 'docker' group: 'sudo usermod -aG docker $USER && newgrp docker' <https://docs.docker.com/engine/install/linux-postinstall/>
💡  Alternatively you could install one of these drivers:
    ▪ kvm2: Not installed: exec: "virsh": executable file not found in $PATH
    ▪ podman: Not installed: exec: "podman": executable file not found in $PATH
    ▪ qemu2: Not installed: exec: "qemu-system-aarch64": executable file not found in $PATH
    ▪ virtualbox: Not installed: unable to find VBoxManage in $PATH

❌  Exiting due to DRV_NOT_HEALTHY: Found driver(s) but none were healthy. See above for suggestions how to fix installed drivers.

tecnomen@debian12:~$ sudo usermod -aG docker $USER && newgrp docker
... loading /etc/bash.bashrc
... loading .bashrc
tecnomen@debian12:~$ 
tecnomen@debian12:~$ minikube start
😄  minikube v1.36.0 on Debian 12.10 (arm64)
✨  Automatically selected the docker driver
📌  Using Docker driver with root privileges
👍  Starting "minikube" primary control-plane node in "minikube" cluster
🚜  Pulling base image v0.0.47 ...
💾  Downloading Kubernetes v1.33.1 preload ...
    > preloaded-images-k8s-v18-v1...:  327.15 MiB / 327.15 MiB  100.00% 18.27 M
    > gcr.io/k8s-minikube/kicbase...:  463.69 MiB / 463.69 MiB  100.00% 25.35 M
🔥  Creating docker container (CPUs=2, Memory=2200MB) ...
🐳  Preparing Kubernetes v1.33.1 on Docker 28.1.1 ...
    ▪ Generating certificates and keys ...
    ▪ Booting up control plane ...
    ▪ Configuring RBAC rules ...
🔗  Configuring bridge CNI (Container Networking Interface) ...
🔎  Verifying Kubernetes components...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🌟  Enabled addons: storage-provisioner, default-storageclass
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
tecnomen@debian12:~$ 
tecnomen@debian12:~$ kubectl get po -A
NAMESPACE     NAME                               READY   STATUS    RESTARTS   AGE
kube-system   coredns-674b8bbfcf-vf9k5           1/1     Running   0          58s
kube-system   etcd-minikube                      1/1     Running   0          64s
kube-system   kube-apiserver-minikube            1/1     Running   0          64s
kube-system   kube-controller-manager-minikube   1/1     Running   0          64s
kube-system   kube-proxy-l2dp6                   1/1     Running   0          59s
kube-system   kube-scheduler-minikube            1/1     Running   0          64s
kube-system   storage-provisioner                1/1     Running   0          63s
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 
tecnomen@debian12:~$ 

```
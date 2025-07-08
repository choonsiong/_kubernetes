# README

- Node is a machine, physical or virtual machine where k8s installed.
- Cluster is a set of nodes group together.
    - Sharing load
    - Failover
- The master node responsible for all worker nodes
- K8S components
    - Master node
        - API server (frontend for k8s)
        - etcd (key-value store)
        - Container runtime (to run container, e.g. docker, rkt, CRI-O)
        - Controller
        - Scheduler
    - Worker node
        - Kubelet (interact with Master node)
    - Command line util `kubectl`
- OCI includes
    - imagespec - container image spec
    - runtimespec - container runtime spec
- `dockershim` allows docker to work with k8s (by passing CRI)
    - CRI is required for k8s to support other container runtime, but docker itself is not CRI compatible
- `containerd` (the daemon manage `runc` part of docker) is CRI compatible
    - k8s (v1.24) removes `dockershim` eventually and supports only `containerd`
- YAML in K8S (`pod-definition.yml`)
    - `apiVersion`
    - `kind`
    - `metadata`
    - `spec`
    - `kubectl create -f pod-definition.yml`
    - `kubectl get pods`
    - `kubectl describe pod myapp-pod`
    ```
    apiVersion: v1
    kind: Pod
    metadata:
        name: myapp-pod
        labels:
            app: myapp
            type: front-end
    spec:
        containers:
            - name: nginx-container
              image: nginx    
    ```          
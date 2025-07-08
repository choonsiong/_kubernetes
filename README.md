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
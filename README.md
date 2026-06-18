# learn-kubernetes

Kubernetes is Master Node Archtecture.
    The components in master are referred as "Master Plane" Components
    The components in node/worker are referred as "Data Plane" Components 

Kubernetes forms the cluster with master node and worknodes. Container workload will be executed on worker nodes only.

# What all components did we learn so far in kubernetes ?

    1) Master Node 
    2) Worker Node 
    3) Control Pane Conponents
    4) Data Pane Conponents
    5) Kubelet 
    6) kuebctl 
    7) kubeapi-server 
    8) etcd 
    9) scheduler 
    10) Controller Manager 

Keep in mind, when you're using kubernetes managed service on cloud, MASTER NODE will be completely under the control of aws and cannot be seen in your account.

In kubernetes, we don't run CONTAINED directly.

We run PODS on the cluster and this pod holds the containers.

Each pod can have one more containers inside the pod.
( Each pod will have an IP, all the containers are on the same network space - they don't have no ip )

POD is the smallest compute resource on kubernetes.

Kubernetes is the first container orchestrator that solved the problem of shared network and storage.

EKS Cluster on AWS is on 3 types:
    1) Public Cluster ( Accessible from the internet and communication from master-node is via public )
    2) Public Private Cluster ( Accessible from the internet & communication from master-node is private )
    3) Private Cluster ( Cannot be accessible from internet, master-node communication is internal )
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

A kubernetes cluster will have multiple nodegroups / nodepools

    What is a nodeGroup ?
        A nodeGroup is nothing but a group of similar instances.

How to connect to the cluster after provisioning ?
    aws eks update-kubeconfig --region <region-code> --name <cluster-name>

What is kube-config ?
    This is a file that containers the cluster info along with authenticationInfo that enables you to connect to the cluster and the location of it in "~/.kube/config"

You need a "kubectl" client package installed on your workStation and then only you can connect to cluster.

How to install kubectl ?
       $ curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
       $ curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
       $ sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
       $ kubectl version --client

    Ref: https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

All the interaction to kubernetes will be done with "kubectl"

How do I know the cluster info that I am connect to ?
    $ kubectl cluster-info
        Kubernetes control plane is running at https://xxxxxxxx.gr7.us-east-1.eks.amazonaws.com
        CoreDNS is running at https://xxxxxxxx.gr7.us-east-1.eks.amazonaws.com/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

        To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.

# What is the syntax of kubectl commands?
    $ kubectl action resource

# Kubernetes config file will have lot of contexts, how do we know the current context of your kube config ?
    $ kubectl config current-context
        arn:aws:eks:us-east-1:xxxxxxxx:cluster/example

# How to generate the context of the cluster:

    $ aws eks update-kubeconfig --region us-east-1 --name 
    ( You can check the generated file in ~/.kube/config )

There are lots of resources in kubernetes, among all POD is smallest computing resource where our workloads are scheduled.

You can create resources on kubernetes either manually or with YAML ( Declarative Format )
    We always prefer creating k8s resource using CODE only

KUBERNETES is all about API's: 
    Based on the type of resource you create, we use the approprivate API.

    $ kubectl cluster-info

This shows the list of resources that can be created on the cluster
    
    $ kubectl api-resources

How to create a pod manually ? Not Recommended!
    $ kubectl run <pod-name> --image=<image-name>
    $ kubectl run welcomepod --image=nginx:latest

How to create or upcate pod with code ?
    $ kubectl create -f fileName.yml ( Just creates if it's not there )
    $ kubectl apply -f fileName.yml ( Creates if it's not there, updates if that's already available )
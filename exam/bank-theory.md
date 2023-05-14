Which component is responsible for scheduling pods to nodes in a Kubernetes cluster?
A) kubelet
B) kube-proxy
C) kube-scheduler
D) kube-apiserver
Answer: C

Which component is responsible for storing and managing the state of the Kubernetes cluster?
A) etcd
B) kube-apiserver
C) kube-controller-manager
D) kube-scheduler
Answer: A

Which component is responsible for ensuring that the desired state of the cluster matches the current state?
A) kube-apiserver
B) kube-controller-manager
C) kube-scheduler
D) kube-proxy
Answer: B

Which component is responsible for managing the networking configuration of pods in a Kubernetes cluster?
A) kube-apiserver
B) kubelet
C) kube-proxy
D) CNI plugin
Answer: D

Which component is responsible for routing traffic to services in a Kubernetes cluster?
A) kube-proxy
B) kubelet
C) kube-controller-manager
D) CNI plugin
Answer: A

Which component is responsible for managing the lifecycle of a containerized application in a Kubernetes cluster?
A) kube-apiserver
B) kube-controller-manager
C) kube-scheduler
D) kubelet
Answer: D

Which component is responsible for authenticating and authorizing API requests in a Kubernetes cluster?
A) kube-apiserver
B) kube-controller-manager
C) kube-scheduler
D) kubelet
Answer: A

What is the default networking mode for Kubernetes?
A) Host Networking
B) Container Networking Interface (CNI)
C) Cluster Networking
D) Service Networking
Answer: B

What is the purpose of a Kubernetes Service?
A) To expose a set of Pods as a network service
B) To provide storage for a set of Pods
C) To schedule Pods onto nodes in the cluster
D) To manage the lifecycle of Pods
Answer: A

What is the purpose of a Kubernetes CNI plugin?
A) To manage the lifecycle of Kubernetes components
B) To provide secure authentication and authorization for Kubernetes applications
C) To manage the networking configuration of Pods
D) To provide storage for Kubernetes applications
Answer: C

What is the purpose of the kube-proxy component in Kubernetes networking?
A) To provide load balancing for Kubernetes Services
B) To manage the lifecycle of Kubernetes components
C) To manage the configuration of Kubernetes networking plugins
D) To monitor the health of the Kubernetes API server
Answer: A

What is the purpose of a Kubernetes Service?
A) To manage and deploy containerized applications
B) To manage and deploy nodes in a cluster
C) To provide a stable IP address and DNS name for a set of pods
D) To schedule pods on a specific node
Answer: C

What is the default type of Kubernetes Service?
A) ClusterIP
B) NodePort
C) LoadBalancer
D) ExternalName
Answer: A

What command is used to create a new deployment in Kubernetes?
A) kubectl create deployment
B) kubectl create deploy
C) kubectl new deployment
D) kubectl deploy create
Answer: A

What option can be used with kubectl get to show additional details about a resource?
A) -v
B) -d
C) -o
D) -a
Answer: C

What command is used to update an existing deployment in Kubernetes?
A) kubectl update deployment
B) kubectl edit deploy
C) kubectl modify deployment
D) kubectl change deploy
Answer: B

What option can be used with kubectl apply to dry-run a configuration change?
A) --simulate
B) --dry-run
C) --preview
D) --test
Answer: B

What command is used to delete a resource in Kubernetes?
A) kubectl delete resource
B) kubectl remove
C) kubectl rm
D) kubectl delete
Answer: D

What option can be used with kubectl logs to tail the logs of a container?
A) -t
B) -f
C) -l
D) -c
Answer: B

Which Kubernetes object is used to manage long-running, stateless applications?
A) Pod
B) Deployment
C) Job
D) DaemonSet
Answer: B) Deployment

What is the purpose of an init container in a pod?
A) It runs before the main container and initializes the environment
B) It runs alongside the main container and shares the same network namespace
C) It runs after the main container and performs cleanup tasks
D) It runs independently of the main container and performs auxiliary tasks
Answer: A) It runs before the main container and initializes the environment

Which Kubernetes object is used to manage batch jobs or one-time processes?
A) Pod
B) Deployment
C) Job
D) DaemonSet
Answer: C) Job

Which Kubernetes object is used to ensure that a specific pod is running on all (or some) nodes in a cluster?
A) Pod
B) Deployment
C) Job
D) DaemonSet
Answer: D) DaemonSet

Which Kubernetes object is used to manage stateful applications that require unique network identifiers and stable storage?
A) Pod
B) Deployment
C) Job
D) StatefulSet
Answer: D) StatefulSet

What is the purpose of a DaemonSet in Kubernetes?
A) To ensure a specified number of replicas of a pod are running
B) To create a one-time job or task
C) To ensure that a copy of a pod is running on each node
D) To create a scalable set of pods that can be horizontally auto-scaled
Answer: C

What is the primary use case for a Kubernetes Job?
A) Running long-lived services or applications
B) Running one-off tasks or batch jobs
C) Scaling up and down replicas of a pod
D) Managing network traffic for a set of pods
Answer: B

How does a Kubernetes Deployment ensure that a desired state is achieved and maintained?
A) By running a set of containers on a single node
B) By automatically scaling up and down replicas of a pod
C) By rolling out changes to a pod in a controlled manner
D) By providing access to external services and resources
Answer: C

What is the purpose of an Init Container in Kubernetes?
A) To provide additional storage volumes to a pod
B) To perform additional setup and configuration before the main container starts
C) To manage the network traffic between pods
D) To provide load balancing for a set of replicas
Answer: B

What is the main difference between a StatefulSet and a Deployment in Kubernetes?
A) StatefulSets are designed for stateless applications, while Deployments are designed for stateful applications
B) StatefulSets ensure that each pod has a stable, unique identity, while Deployments do not
C) StatefulSets allow for horizontal scaling, while Deployments do not
D) StatefulSets provide access to external resources, while Deployments do not
Answer: B

What is the main advantage of using a Job in Kubernetes for running a batch process?
A) It allows for running the process on a specific node
B) It automatically retries the process if it fails
C) It ensures that the process completes successfully before terminating
D) It provides real-time monitoring and logging of the process
Answer: C

What is the purpose of a Kubernetes volume?
A) To provide persistent storage for a container
B) To store configuration data for a container
C) To store secrets for a container
D) To store log files for a container
Answer: A) To provide persistent storage for a container

Which Kubernetes resource is used to request storage for a pod?
A) Pod
B) Deployment
C) Persistent Volume
D) Persistent Volume Claim
Answer: D) Persistent Volume Claim

What is a Persistent Volume in Kubernetes?
A) A request for storage made by a pod
B) A block of storage that can be requested by a pod
C) A type of Kubernetes object used to store configuration data
D) A Kubernetes object that represents a secret
Answer: B) A block of storage that can be requested by a pod

Which Kubernetes resource is used to represent a volume that has been manually created by a cluster administrator?
A) ConfigMap
B) Secret
C) Persistent Volume
D) Persistent Volume Claim
Answer: C) Persistent Volume

Which Kubernetes resource is used to bind a Persistent Volume to a Persistent Volume Claim?
A) Pod
B) Deployment
C) Persistent Volume
D) Storage Class
Answer: C) Persistent Volume

What is the purpose of a ConfigMap in Kubernetes?
A) To store configuration data for a container
B) To store secrets for a container
C) To provide persistent storage for a container
D) To store log files for a container
Answer: A) To store configuration data for a container

Which Kubernetes resource is used to represent a sensitive piece of information, such as a password or API key?
A) ConfigMap
B) Secret
C) Persistent Volume
D) Persistent Volume Claim
Answer: B) Secret

What is the purpose of a Secret in Kubernetes?
A) To store configuration data for a container
B) To store secrets for a container
C) To provide persistent storage for a container
D) To store log files for a container
Answer: B) To store secrets for a container

Which Kubernetes resource is used to specify configuration data that can be consumed by a container?
A) ConfigMap
B) Secret
C) Persistent Volume
D) Persistent Volume Claim
Answer: A) ConfigMap

What is an example of a use case for an Init Container in Kubernetes?
A) Running a script that configures a database before the main container starts
B) Running a sidecar container that handles logging for the main container
C) Running a container that shares a volume with the main container
D) Running a container that monitors the health of the main container
Answer: A) Running a script that configures a database before the main container starts

What is the correct command to apply changes made to a Kubernetes manifest file?
A) kubectl update -f file.yaml
B) kubectl apply -f file.yaml
C) kubectl edit -f file.yaml
D) kubectl replace -f file.yaml
Answer: B) kubectl apply -f file.yaml

Which command can be used to view the logs of a pod?
A) kubectl logs
B) kubectl view
C) kubectl describe
D) kubectl get
Answer: A) kubectl logs

What is the recommended way to manage Kubernetes objects in a declarative manner?
A) Using imperative commands
B) Editing the manifest files directly on the server
C) Using kubectl apply with manifest files
D) Using kubectl create with manifest files
Answer: C) Using kubectl apply with manifest files

Which command can be used to edit an existing Kubernetes object in place?
A) kubectl create
B) kubectl replace
C) kubectl apply
D) kubectl edit
Answer: D) kubectl edit

Which kubectl command can be used to view detailed information about a specific object?
A) kubectl get
B) kubectl view
C) kubectl describe
D) kubectl logs
Answer: C) kubectl describe

What is the recommended way to set up an environment variable for a container in a pod?
A) By editing the manifest file directly
B) By using a ConfigMap or Secret
C) By using the kubectl set env command
D) By using the kubectl edit command
Answer: B) By using a ConfigMap or Secret

Which command can be used to delete a Kubernetes object?
A) kubectl delete
B) kubectl remove
C) kubectl erase
D) kubectl discard
Answer: A) kubectl delete

What is the syntax for specifying a specific namespace when running kubectl commands?
A) --namespace=<namespace>
B) -namespace <namespace>
C) /namespace=<namespace>
D) -n <namespace>
Answer: D) -n <namespace>

Which kubectl command can be used to generate a YAML or JSON representation of a Kubernetes object?
A) kubectl describe
B) kubectl edit
C) kubectl get
D) kubectl export
Answer: D) kubectl export

Which command can be used to view the current status of a Kubernetes object?
A) kubectl get
B) kubectl view
C) kubectl describe
D) kubectl status
Answer: A) kubectl get

You have a Job that runs a batch process that takes several hours to complete. The process has failed, but you need to ensure that it is completed successfully. What is the best way to restart the Job and ensure that it completes successfully?
A) Use the kubectl delete job command to delete the job and then recreate it.
B) Use the kubectl apply command to apply a new manifest with the same Job.
C) Use the kubectl edit job command to change the restart policy to "OnFailure" and then delete and recreate the failed pod.
D) Use the kubectl rollout restart command to restart the Job.

You have a Kubernetes pod that needs to access a database running outside the Kubernetes cluster. Which Kubernetes object can you use to securely pass the database credentials to the pod?
A) Pod
B) Secret
C) ConfigMap
D) ServiceAccount
Answer: B

You created a PersistentVolumeClaim and used it to mount a PersistentVolume in a Pod. However, you noticed that the Pod is stuck in the Pending state and the PersistentVolumeClaim is in the Pending state as well. What Kubernetes feature can you use to troubleshoot the issue?
A. kubectl get events
B. kubectl logs
C. kubectl describe pod
D. kubectl edit pvc

Answer: A
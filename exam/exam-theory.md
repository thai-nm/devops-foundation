1. Which component is responsible for scheduling pods to nodes in a Kubernetes cluster?
A) kubelet
B) kube-proxy
C) kube-scheduler
D) kube-apiserver
Answer: C

2. Which component is responsible for storing and managing the state of the Kubernetes cluster?
A) etcd
B) kube-apiserver
C) kube-controller-manager
D) kube-scheduler
Answer: A

3. Which component is responsible for ensuring that the desired state of the cluster matches the current state?
A) kube-apiserver
B) kube-controller-manager
C) kube-scheduler
D) kube-proxy
Answer: B

4. Which component is responsible for managing the networking configuration of pods in a Kubernetes cluster?
A) kube-apiserver
B) kubelet
C) kube-proxy
D) CNI plugin
Answer: D

5. Which component is responsible for routing traffic to services in a Kubernetes cluster?
A) kube-proxy
B) kubelet
C) kube-controller-manager
D) CNI plugin
Answer: A

6. Which component is responsible for managing the lifecycle of a containerized application in a Kubernetes cluster?
A) kube-apiserver
B) kube-controller-manager
C) kube-scheduler
D) kubelet
Answer: D

7. Which component is responsible for authenticating and authorizing API requests in a Kubernetes cluster?
A) kube-apiserver
B) kube-controller-manager
C) kube-scheduler
D) kubelet
Answer: A

8. What is the default networking mode for Kubernetes?
A) Host Networking
B) Container Networking Interface (CNI)
C) Cluster Networking
D) Service Networking
Answer: B

9. What is the purpose of a Kubernetes Service?
A) To expose a set of Pods as a network service
B) To provide storage for a set of Pods
C) To schedule Pods onto nodes in the cluster
D) To manage the lifecycle of Pods
Answer: A

10. What is the purpose of a Kubernetes CNI plugin?
A) To manage the lifecycle of Kubernetes components
B) To provide secure authentication and authorization for Kubernetes applications
C) To manage the networking configuration of Pods
D) To provide storage for Kubernetes applications
Answer: C

11. What is the purpose of the kube-proxy component in Kubernetes networking?
A) To provide load balancing for Kubernetes Services
B) To manage the lifecycle of Kubernetes components
C) To manage the configuration of Kubernetes networking plugins
D) To monitor the health of the Kubernetes API server
Answer: A

12. What is the purpose of a Kubernetes Service?
A) To manage and deploy containerized applications
B) To manage and deploy nodes in a cluster
C) To provide a stable IP address and DNS name for a set of pods
D) To schedule pods on a specific node
Answer: C

13. What is the default type of Kubernetes Service?
A) ClusterIP
B) NodePort
C) LoadBalancer
D) ExternalName
Answer: A

14. What command is used to create a new deployment in Kubernetes?
A) kubectl create deployment
B) kubectl create deploy
C) kubectl new deployment
D) kubectl deploy create
Answer: A

15. What option can be used with kubectl get to show additional details about a resource?
A) -v
B) -d
C) -o
D) -a
Answer: C

16. What command is used to update an existing deployment in Kubernetes?
A) kubectl update deployment
B) kubectl edit deploy
C) kubectl modify deployment
D) kubectl change deploy
Answer: B

17. What option can be used with kubectl apply to dry-run a configuration change?
A) --simulate
B) --dry-run
C) --preview
D) --test
Answer: B

18. What command is used to delete a resource in Kubernetes?
A) kubectl delete resource
B) kubectl remove
C) kubectl rm
D) kubectl delete
Answer: D

19. What option can be used with kubectl logs to tail the logs of a container?
A) -t
B) -f
C) -l
D) -c
Answer: B

20. Which Kubernetes object is used to manage long-running, stateless applications?
A) Pod
B) Deployment
C) Job
D) DaemonSet
Answer: B) Deployment

21. What is the purpose of an init container in a pod?
A) It runs before the main container and initializes the environment
B) It runs alongside the main container and shares the same network namespace
C) It runs after the main container and performs cleanup tasks
D) It runs independently of the main container and performs auxiliary tasks
Answer: A) It runs before the main container and initializes the environment

22. Which Kubernetes object is used to manage batch jobs or one-time processes?
A) Pod
B) Deployment
C) Job
D) DaemonSet
Answer: C) Job

23. Which Kubernetes object is used to ensure that a specific pod is running on all (or some) nodes in a cluster?
A) Pod
B) Deployment
C) Job
D) DaemonSet
Answer: D) DaemonSet

24. Which Kubernetes object is used to manage stateful applications that require unique network identifiers and stable storage?
A) Pod
B) Deployment
C) Job
D) StatefulSet
Answer: D) StatefulSet

25. What is the purpose of a DaemonSet in Kubernetes?
A) To ensure a specified number of replicas of a pod are running
B) To create a one-time job or task
C) To ensure that a copy of a pod is running on each node
D) To create a scalable set of pods that can be horizontally auto-scaled
Answer: C

26. What is the primary use case for a Kubernetes Job?
A) Running long-lived services or applications
B) Running one-off tasks or batch jobs
C) Scaling up and down replicas of a pod
D) Managing network traffic for a set of pods
Answer: B

27. How does a Kubernetes Deployment ensure that a desired state is achieved and maintained?
A) By running a set of containers on a single node
B) By automatically scaling up and down replicas of a pod
C) By rolling out changes to a pod in a controlled manner
D) By providing access to external services and resources
Answer: C

28. What is the main difference between a StatefulSet and a Deployment in Kubernetes?
A) StatefulSets are designed for stateless applications, while Deployments are designed for stateful applications
B) StatefulSets ensure that each pod has a stable, unique identity, while Deployments do not
C) StatefulSets allow for horizontal scaling, while Deployments do not
D) StatefulSets provide access to external resources, while Deployments do not
Answer: B

29. What is the purpose of a Kubernetes volume?
A) To provide persistent storage for a container
B) To store configuration data for a container
C) To store secrets for a container
D) To store log files for a container
Answer: A) To provide persistent storage for a container

30. Which Kubernetes resource is used to request storage for a pod?
A) Pod
B) Deployment
C) Persistent Volume
D) Persistent Volume Claim
Answer: D) Persistent Volume Claim

31. What is a Persistent Volume in Kubernetes?
A) A request for storage made by a pod
B) A block of storage that can be requested by a pod
C) A type of Kubernetes object used to store configuration data
D) A Kubernetes object that represents a secret
Answer: B) A block of storage that can be requested by a pod

32. What is the purpose of a ConfigMap in Kubernetes?
A) To store configuration data for a container
B) To store secrets for a container
C) To provide persistent storage for a container
D) To store log files for a container
Answer: A) To store configuration data for a container

33. Which Kubernetes resource is used to represent a sensitive piece of information, such as a password or API key?
A) ConfigMap
B) Secret
C) Persistent Volume
D) Persistent Volume Claim
Answer: B) Secret

34. What is the correct command to apply changes made to a Kubernetes manifest file?
A) kubectl update -f file.yaml
B) kubectl apply -f file.yaml
C) kubectl edit -f file.yaml
D) kubectl replace -f file.yaml
Answer: B) kubectl apply -f file.yaml

35. Which command can be used to view the logs of a pod?
A) kubectl logs
B) kubectl view
C) kubectl describe
D) kubectl get
Answer: A) kubectl logs

36. Which kubectl command can be used to view detailed information about a specific object?
A) kubectl get
B) kubectl view
C) kubectl describe
D) kubectl logs
Answer: C) kubectl describe

37. You have a Job that runs a batch process that takes several hours to complete. The process has failed, but you need to ensure that it is completed successfully. What is the best way to restart the Job and ensure that it completes successfully?
A) Use the kubectl delete job command to delete the job and then recreate it.
B) Use the kubectl apply command to apply a new manifest with the same Job.
C) Use the kubectl edit job command to change the restart policy to "OnFailure" and then delete and recreate the failed pod.
D) Use the kubectl rollout restart command to restart the Job.

38. You have a Kubernetes pod that needs to access a database running outside the Kubernetes cluster. Which Kubernetes object can you use to securely pass the database credentials to the pod?
A) Pod
B) Secret
C) ConfigMap
D) ServiceAccount
Answer: B

39. You created a PersistentVolumeClaim and used it to mount a PersistentVolume in a Pod. However, you noticed that the Pod is stuck in the Pending state and the PersistentVolumeClaim is in the Pending state as well. What Kubernetes feature can you use to troubleshoot the issue?
A. kubectl get events
B. kubectl logs
C. kubectl describe pod
D. kubectl edit pvc
Answer: A

40. You have a pod running in your cluster, but it is not responding to requests. You suspect that it may have crashed. Which kubectl command can you use to check the status of the pod?
A. kubectl get pods
B. kubectl describe pod
C. kubectl logs
D. kubectl exec
Answer: B. kubectl describe pod
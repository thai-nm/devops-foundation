Deploy a messaging pod using the redis:alpine image with the labels set to tier=msg.
Create a service messaging-service to expose the messaging application within the cluster on port 6379.
Create a static pod named static-busybox on the controlplane node that uses the busybox image and the command sleep 1000.
Expose the hr-web-app as service hr-web-app-service application on port 30082 on the nodes on the cluster.
Create a Pod called redis-storage with image: redis:alpine with a Volume of type emptyDir that lasts for the life of the Pod.
Create a new deployment called nginx-deploy, with image nginx:1.16 and 1 replica. Next upgrade the deployment to version 1.17 using rolling update.
Create a nginx pod called nginx-resolver using image nginx, expose it internally with a service called nginx-resolver-service. Test that you are able to look up the service and pod names from within the cluster. Use the image: busybox:1.28 for dns lookup.
Create a static pod on node01 called nginx-critical with image nginx and make sure that it is recreated/restarted automatically in case of a failure.

Create a pod called multi-pod with two containers.
  Container 1, name: alpha, image: nginx
  Container 2: name: beta, image: busybox, command: sleep 4800

Environment Variables:
  Container 1:
    name: alpha

  Container 2:
    name: beta

Create a pod called hr-pod in hr namespace belonging to the production environment and frontend tier .
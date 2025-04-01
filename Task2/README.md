**Task 2: K8s App restrictions over network**

Description:
- my-app-deployment and cache-deployment deployed, and my-app-deployment
deployment exposed through a service named my-app-service . Create a
NetworkPolicy named my-app-network-policy to restrict incoming and outgoing traffic
to my-app-deployment pods with the following specifications:
- Allow incoming traffic only from pods within the same namespace.
- Allow incoming traffic from a specific pod with the label app=trusted
- Allow outgoing traffic to pods within the same namespace.
- Deny all other incoming and outgoing traffic.
Based on the above requirement, following are the steps that we can follow for the K8s application to run:

**Step 1: Create the Kubernetes Deployments and Service**
First, we need to define the Kubernetes Deployment YAML for both my-app-deployment and cache-deployment. They are defined as my-app-deployment.yaml and cache-deployment.yaml in Task2 folder

**Step 2: Expose my-app-deployment via a Service**
Next, define a service to expose my-app-deployment: This is defined as my-app-service.yaml

**Step 3: Create the NetworkPolicy**
The next step is creating a NetworkPolicy that restricts traffic according to the requirements. It is defined as my-app-network-policy.yaml

**Step 4: Apply the configurations**
Now that you have the YAML files for the deployments, service, and network policy, you can apply them to your Kubernetes cluster.

- Apply the deployments
kubectl apply -f my-app-deployment.yaml
kubectl apply -f cache-deployment.yaml

- Apply the service
kubectl apply -f my-app-service.yaml

- Apply the network policy
kubectl apply -f my-app-network-policy.yaml

**Step 5: Verify the Deployment and Network Policy**
After applying the YAML files, verify that everything has been deployed correctly.
- Check the deployments with command:

kubectl get deployments

You should see both my-app-deployment and cache-deployment in the list.

- Check the service with command :
kubectl get svc

Verify that my-app-service is created.

- Check the network policy with command:
kubectl get networkpolicy

This will show you if the my-app-network-policy was successfully applied.

**Step 6: Additional Considerations**
Labeling the trusted pods: For the network policy to work as expected, ensure that you label the trusted pods correctly with the following command

kubectl label pod app=trusted

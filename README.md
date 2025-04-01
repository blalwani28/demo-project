This is a demo project for practical test. It has 2 tasks. Following is the task description: 

**Task 1:**: **Simple Node Js Application Deployment on Docker container**
Description:
- Create a Dockerfile for a simple Node.js application that listens on port 3000. The
Dockerfile should use a lightweight base image, install dependencies, copy the
application code, and specify the command to run the application.

**Steps:**
Step 1: Install Docker
First, make sure that Docker is installed on your system. You can download it from the official website:
https://docs.docker.com/get-started/get-docker 

Step2: Create DockerFile
We have created the DockerFile in the Task1 folder to run the Node.js application.

Step 3: Build the Docker Image
Once you have your Dockerfile ready, you can build the Docker image using the docker build command. Navigate to the directory where the Dockerfile is located and run the command

docker build -t my-image-name .

-t my-image-name: This gives your image a tag (name).

.: The dot tells Docker to look for the Dockerfile in the current directory.

Step 4: Verify the Image Was Created
Once the build is complete, you can check the list of images on your system with:

docker images

Step 5: Run the Docker Image (Create a Container)
Now that the image is built, you can run a container from it using the docker run command:

docker run -p 3000:3000 node-app

Step 6: Verify the Container is Running
To check if your container is running, use:

docker ps

Step 7: Access the Application

As you have exposed a port 3000, you should be able to access the application in your browser by going to:

http://localhost:3000



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

1. Create the Kubernetes Deployments and Service

First, we need to define the Kubernetes Deployment YAML for both my-app-deployment and cache-deployment. They are defined as my-app-deployment.yaml and cache-deployment.yaml in Task2 folder

2. Expose my-app-deployment via a Service
Next, define a service to expose my-app-deployment: This is defined as my-app-service.yaml

3. Create the NetworkPolicy
The next step is creating a NetworkPolicy that restricts traffic according to the requirements. It is defined as my-app-network-policy.yaml

4. Apply the configurations
Now that you have the YAML files for the deployments, service, and network policy, you can apply them to your Kubernetes cluster.

# Apply the deployments
kubectl apply -f my-app-deployment.yaml
kubectl apply -f cache-deployment.yaml

# Apply the service
kubectl apply -f my-app-service.yaml

# Apply the network policy
kubectl apply -f my-app-network-policy.yaml

5. Verify the Deployment and Network Policy
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

6. Additional Considerations
Labeling the trusted pods: For the network policy to work as expected, ensure that you label the trusted pods correctly.

kubectl label pod <trusted-pod-name> app=trusted

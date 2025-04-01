**Task 1:: Simple Node Js Application Deployment on Docker container** 

Description:
- Create a Dockerfile for a simple Node.js application that listens on port 3000. The
Dockerfile should use a lightweight base image, install dependencies, copy the
application code, and specify the command to run the application.


**Step 1: Install Docker** 
First, make sure that Docker is installed on your system. You can download it from the official website: https://docs.docker.com/get-started/get-docker

**Step2: Create DockerFile**
We have created the DockerFile in the Task1 folder to run the Node.js application.

**Step 3: Build the Docker Image**
Once you have your Dockerfile ready, you can build the Docker image using the docker build command. 
Navigate to the directory where the Dockerfile is located and run the command

- docker build -t my-image-name .

-t my-image-name: This gives your image a tag (name).

.: The dot tells Docker to look for the Dockerfile in the current directory.

**Step 4: Verify the Image Was Created**
Once the build is complete, you can check the list of images on your system with:

- docker images

**Step 5: Run the Docker Image (Create a Container)**
Now that the image is built, you can run a container from it using the docker run command:

- docker run -p 3000:3000 node-app

**Step 6: Verify the Container is Running**
To check if your container is running, use:

- docker ps

**Step 7: Access the Application**

As you have exposed a port 3000, you should be able to access the application in your browser by going to:

http://localhost:3000

# Use the official Node.js image from the Docker Hub (Alpine version for smaller size)
FROM node:alpine

# Set the working directory in the container
WORKDIR /app

# Copy the package.json and package-lock.json (if available) to the container
COPY package*.json ./

# Install the application dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Expose the port the app will run on
EXPOSE 3000

# Set the command to run the Node.js application
CMD ["npm", "start"]

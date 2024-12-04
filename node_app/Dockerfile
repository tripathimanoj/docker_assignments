# Use the official Node.js image from the Docker Hub
FROM node:16-slim

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and install dependencies
COPY package.json /app
RUN npm install

# Copy the app dir code into the container
COPY . /app

# Expose port 3000 for the app to run
EXPOSE 3000

# Command to run the Node.js app
CMD ["npm", "start"]

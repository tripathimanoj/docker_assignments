
# Docker Assignments 
## https://docs.google.com/document/d/1iYoB8YtFzlcmd2KYUoR_iw2Ek3bXhh6nFfKJZ4OCkZw/edit?tab=t.0

# Docker Assignments Solution...

## Assignment 1: Dockerizing a Flask Application

 https://github.com/03sarath/mlops-specialization-assignments/blob/master/docker-assignment/Assignments/Dockerizing%20a%20Flask%20Application.md

## solution | Here i am using linux instance (Amazon Linux2) in aws cloud .

**Step 1:**
create a ubuntu instance in aws cloud.

**Step 2:** 
install git and docker and upload folder structure to aws instance ie via git or via ssh.

```
sudo yum update -y

sudo amazon-linux-extras install docker

sudo service docker start

sudo usermod -a -G docker ec2-user

docker --version
```

--screen shot

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss1.png)

**Step 3:**  
create a docker file:

[ec2-user@ip-172-31-10-202 file_uploads]$ cat Dockerfile
```
-# Use the official Python image from the Docker Hub
FROM python:3.9-slim

-# Set the working directory in the container
WORKDIR /app

-# Copy the application code into the container
COPY . /app

-# Copy the requirements file and install dependencies
RUN pip install --no-cache-dir -r requirements.txt

-# Expose port 5000
EXPOSE 5000

-# Define environment variable
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0

-# Run app.py when the container launches
CMD ["flask", "run"]
```

[ec2-user@ip-172-31-10-202 file_uploads]$

--screen shot

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss2.png)

**Step 4:**

build docker image and run that container:
```
docker build -t file_uploads .
docker run -p 5000:5000 gile_uploads
```

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/docker0.png)

**Step 5:**

 update aws instance inbound rule instance > security group >inbound rule 
 add a new tcp rule with port 5000 and save 

--screen shot

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss3.png)

**Step 6:**

 then access file by instance public ip4:5000 ex http://13.203.103.98:5000/

 --screen shot

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss4.png)

 

 #############################

  ## Assignment 2: Dockerizing a Node.js Application with Environment Variables

 https://github.com/03sarath/mlops-specialization-assignments/blob/master/docker-assignment/Assignments/Dockerizing%20a%20Node.js%20Application%20with%20Environment%20Variables.md

## solution

**Step 1** and **Step 2** are same as above

**Step 3:**
create a docker file:

```
[ec2-user@ip-172-31-10-202 node_app]$ cat Dockerfile
# Use the official Node.js image from the Docker Hub
FROM node:16-slim

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and install dependencies
COPY package.json /app
RUN npm install

# Copy the application code into the container
COPY . /app

# Expose port 3000 for the app to run
EXPOSE 3000

# Command to run the Node.js app
CMD ["npm", "start"]
[ec2-user@ip-172-31-10-202 node_app]$
```
screen shot

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss5.png)

**Step 4: **

update aws instance inbound rule instance > security group >inbound rule 
add a new tcp rule with port 3000 and save [As same as in above assignment]

**Step 5:** 

run the docker build and run command to execute the container.

```

docker build -t node_app .
docker run -e GREETING='Welcome to Docker!' -p 3000:3000 node_app

```

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss6.png)

and access the node application via instance ip4:3000 ex  http://13.203.103.98:3000/

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss7.png)


##################################

## Assignment 3: Dockerizing a breast cancer ML model

https://github.com/03sarath/mlops-specialization-assignments/blob/master/docker-assignment/Assignments/Dockerizing%20%20a%20breast%20cancer%20ML%20model.md

## solution

**Step 1** and **Step 2** are same as above

**Step 3:**
create a docker file:

```
# Use the official Python image from the Docker Hub
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Expose the port the app runs on
EXPOSE 9696

# Run the Flask app
CMD ["python", "predict.py"]
```
screen shot

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss8.png)

**Step 4:**

update aws instance inbound rule instance > security group >inbound rule 
add a new tcp rule with port 3000 and save [As same as in above assignment]

**Step 5:**

run the docker build and run command to execute the container.

```

docker build -t breast_cancer_app .
docker run -d -p 9696:9696 breast_cancer_app
python predict-test.py

```
After running container in detach mode now we can run the another command so that it takes the input to the docker container and return the possible prediction.

screen shot

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss9.png)

#########################################################

## Assignment 4: Dockerizing Flask app

https://github.com/03sarath/docker-node-app/blob/main/getting-started-example.md

## solution

**Step 1** and **Step 2** are same as above

**Step 3**
create a docker file:

```
# Use an official Python runtime as a parent image
FROM python:3.8-slim

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the current directory contents into the container at the working directory
COPY . .

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Make port 5000 available to the world outside this container
EXPOSE 5000

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
```

**Step 4:**

run the following docker commands

```
docker build -t python-flask-sample .
docker run -p 5000:5000 python-flask-sample
```

-- screen shot

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss10.png)

**Step 5:**

Access the flask app by instance ip4:5000 ex 13.203.103.98:5000

--screen shot 

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss11.png)

# End Of Assignments ------------------------

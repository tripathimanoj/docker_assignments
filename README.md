
# Docker Assignments


## Assignment 1: Dockerizing a Flask Application

 https://github.com/03sarath/mlops-specialization-assignments/blob/master/docker-assignment/Assignments/Dockerizing%20a%20Flask%20Application.md

## solution | Here i am using linux instance (Amazon Linux2) in aws cloud .

step1: create a ubuntu instance in aws cloud.

step2: install git and docker and upload folder structure to aws instance ie via git or via ssh.

sudo yum update -y

sudo amazon-linux-extras install docker

sudo service docker start

sudo usermod -a -G docker ec2-user

docker --version

--screen shot 1 

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss1.png)

step3 create a docker file:

[ec2-user@ip-172-31-10-202 file_uploads]$ cat Dockerfile
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

[ec2-user@ip-172-31-10-202 file_uploads]$

--screen shot 2

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss2.png)

step 3

build docker image and run that container:

docker build -t file_uploads .
docker run -p 5000:5000 gile_uploads

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/docker0.png)
 step 4 

 update aws instance inbound rule instance > security group >inbound rule 
 add a new tcp rule with port 5000 and save 

screen shot 4

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss3.png)

step 5 

 then access file by instance public ip4:5000 ex http://13.203.103.98:5000/

 screen shot 3

![Docker Assignment Image](https://raw.githubusercontent.com/tripathimanoj/docker_assignments/main/dockerss4.png)

 

 #############################

 ## Assignment 2: Dockerizing a Node.js Application with Environment Variables

 https://github.com/03sarath/mlops-specialization-assignments/blob/master/docker-assignment/Assignments/Dockerizing%20a%20Node.js%20Application%20with%20Environment%20Variables.md

## solution

step1: create a ubuntu instance in aws cloud.

step2: install git and docker and upload folder structure to aws instance ie via git or via ssh.

sudo yum update -y
sudo amazon-linux-extras install docker
sudo service docker start
sudo usermod -a -G docker ec2-user
docker --version

--screen shot 1 

step3 create a docker file:

## Cloud DevOps nanodegree: Capstone project
### Project Overview
In this project, the skills developed throughout the Cloud DevOps Nanodegree program will be tested:

* Working in AWS
* Using Jenkins to implement Continuous Integration and Continuous  Deployment
* Building pipelines
* Working with Ansible/CloudFormation to deploy clusters
* Building Kubernetes clusters
* Building Docker containers in pipelines

### Setting AWS infrastructure
To create the EKS cluster:
`cd Infrastructure/`
`make kubernetes-cluster`
![alt text](doc/EKS-cluster.png)


### Linting stage check
* Dockerfile linting error:
![alt text](doc/Dockerfile_Linting_Error.png)
* HTML file linting erro:
![alt text](doc/Html_Linting_Error.png)
* Linting OK:
![alt text](doc/Linting_OK.png)

### Jenkins server
A Jenkins server was allocated within a EC2 instance, and an elastic IP was addressed to it:
![alt text](doc/ElasticIP-JenkinsServer.png)

### EC2 Instances
There were generated 4 EC2 instances. One of them was the Jenkins server and the rest were part of the EKS cluster:
![alt text](doc/EC2_Instances.png)

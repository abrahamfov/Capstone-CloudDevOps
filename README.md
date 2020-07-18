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
From Infrastructure folder:

* Create the network stack:

    `./create.sh capstone-network ./network.yml ./network-parameters.json`

* Create the eks cluster stack:

    `./create.sh capstone-cluster ./eks-cluster.yml ./eks-cluster-parameters.json`

* Create the nodegroup stack for the cluster:

    `./create.sh capstone-cluster ./eks-nodegroup.yml ./eks-nodegroup-parameters.json`

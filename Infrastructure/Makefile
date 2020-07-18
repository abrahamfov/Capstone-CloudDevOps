# Instructions for creation of the Kubernetes-Cluster in AWS::EKS. This is intended
# To be used after installing the aws cli and configuring aws credentials
# in the Jenkins server.
kubernetes-cluster:
	eksctl create cluster --name aortiz-capstone --version 1.16 \
	--nodegroup-name standard-workers --node-type t2.micro --nodes 3 \
	--nodes-min 1 --nodes-max 4 --node-ami auto --region eu-west-3
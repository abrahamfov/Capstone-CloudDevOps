pipeline {
    agent any
    stages {
        stage ('Lint artifacts'){
            steps {
                sh 'hadolint --ignore DL3007 Dockerfile'
                sh 'tidy -q -e *.html'
            }
        }
        stage ('Build docker image'){
            steps {
                sh 'docker build -t aortiz-capstone .'
            }
        }
        stage ('Push docker image'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]){
                    sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                    sh 'docker push abrahamfov/aortiz-capstone'
                }
            }
        }
        stage ('Deploy container'){
            steps{
                withAWS(credentials: 'aws-key', region: 'eu-west-3') {
                sh 'aws s3 ls'
                // aws eks --region eu-central-1 update-kubeconfig --name UdacityCapstoneProjectKubernetesCluster
	            // kubectl config use-context arn:aws:eks:eu-central-1:793553224113:cluster/UdacityCapstoneProjectKubernetesCluster

                // arn:aws:eks:eu-west-3:749371973534:cluster/CapstoneEKS-6iaKho2MJ8Zt

                // sh 'aws eks --region eu-west-3 update-kubeconfig --name aortiz-capstone-EKS'
  		        // sh 'kubectl apply -f Infrastructure/aws-auth-cm.yaml'
  		        // sh 'kubectl apply -f deployment.yml'
  		        // sh 'kubectl get nodes'
  		        // sh 'kubectl get pods -o wide'
                }
            }
        }
    }
}
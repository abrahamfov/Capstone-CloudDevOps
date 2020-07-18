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
                    sh 'aws eks --region eu-west-3 update-kubeconfig --name aortiz-capstone'
                    sh 'kubectl config use-context arn:aws:eks:eu-west-3:749371973534:cluster/aortiz-capstone'
                    sh 'kubectl set image deployments/aortiz-capstone aortiz-capstone=abrahamfov/aortiz-capstone:latest'
                    sh 'kubectl apply -f Infrastructure/deployment-lb.yml'
                    sh 'kubectl get nodes'
                    sh 'kubectl get deployment'
                    sh 'kubectl get pods -o wide'
                    sh 'kubectl get service/aortiz-capstone'
                    sh 'kubectl rollout status deployment aortiz-capstone'
                }
            }
        }
    }
}
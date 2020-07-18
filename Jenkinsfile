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
                withDockerRegistry([url:"",credentialsId:"dockerhub"]){
                    sh "docker tag aortiz-capstone abrahamfov/aortiz-capstone"
                    sh 'docker push abrahamfov/aortiz-capstone'
                }
            }
        }
    }
}
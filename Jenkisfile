pipeline {
    agent any
    stages {
        stage ('Lint Dockerfile){
            steps {
                sh 'hadolint Dockerfile'
            }
        }
        stage ('Lint HMTL'){
            steps {
                sh 'tidy -q -e *.html'
            }
        }
    }
}
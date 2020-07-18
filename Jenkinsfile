pipeline {
    agent any
    stages {
        stage ('Lint Dockerfile'){
            steps {
                sh 'hadolint --ignore DL3007 Dockerfile'
                sh 'tidy -q -e *.html'
            }
        }
    }
}
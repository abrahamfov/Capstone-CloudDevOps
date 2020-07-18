pipeline {
    agent any
    stages {
        stage ('Lint artifacts'){
            steps {
                sh 'hadolint --ignore DL3007 Dockerfile'
                sh 'tidy -q -e *.html'
            }
        }
    }
}
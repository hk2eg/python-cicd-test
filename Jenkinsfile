pipeline {
    agent {
        label 'jenkins-agent-1'
    }
    environment {
        IMAGE_NAME = 'python-ci-demo'
    }
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:$BUILD_NUMBER .'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'docker run --rm -v $PWD:/app $IMAGE_NAME:$BUILD_NUMBER'
            }
        }
    }
    post {
        always {
            junit 'results.xml'
        }
    }
}

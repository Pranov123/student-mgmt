pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t hello-java:latest .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run --rm hello-java:latest'
            }
        }
    }
}

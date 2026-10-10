pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Maven Test') {
            steps {
                bat 'mvn clean test'
            }
        }

        stage('Maven Package') {
            steps {
                bat 'mvn package -DskipTests'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t student-mgmt:latest .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker run --rm student-mgmt:latest'
            }
        }
    }
}

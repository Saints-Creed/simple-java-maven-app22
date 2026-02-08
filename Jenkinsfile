pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application (simulation)...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}

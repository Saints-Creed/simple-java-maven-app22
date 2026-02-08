pipeline {
    agent any   // Uses a specific agent (any available Jenkins agent)

    options {
        timestamps()               // Store build logs with timestamps
        skipDefaultCheckout(true)  // Explicit checkout stage
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/jenkins-docs/simple-java-maven-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            when {
                success()   // Deploy only if previous stages succeed
            }
            steps {
                echo "Deploying application (simulation)..."
                echo "Application deployed successfully!"
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }

        failure {
            echo 'Pipeline failed!'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}

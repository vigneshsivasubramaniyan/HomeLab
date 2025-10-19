pipeline {
    agent any

    stages {
        stage('Test Webhook') {
            steps {
                echo "✅ Webhook received and Jenkins pipeline triggered!"
                // Optional: check Docker version to ensure Jenkins can access Docker
                sh 'docker --version || echo "Docker not accessible"'
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline ran successfully!"
        }
        failure {
            echo "❌ Pipeline failed!"
        }
    }
}

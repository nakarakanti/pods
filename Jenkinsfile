pipeline {
    agent any

    stages {
        stage('Initial Setup') {
            steps {
                echo 'Starting the build process...'
                // Add your initial setup steps here
            }
        }

        stage('Fetch Artifact') {
            steps {
                echo 'Fetching the artifact from the repository...'
                // Simulate artifact fetching
                sh 'echo "Fetching artifact..."'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                // Simulate build process
                sh 'echo "Building the project..."'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Simulate running tests
                sh 'echo "Running tests..."'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the project...'
                // Simulate deployment
                sh 'echo "Deploying the project..."'
            }
        }

        stage('Cleanup') {
            steps {
                echo 'Cleaning up workspace...'
                // Simulate cleanup
                sh 'echo "Cleaning up workspace..."'
            }
        }
    }

    post {
        always {
            echo 'This will always run after the stages.'
        }
        success {
            echo 'This will run only if the pipeline succeeds.'
        }
        failure {
            echo 'This will run only if the pipeline fails.'
        }
    }
}

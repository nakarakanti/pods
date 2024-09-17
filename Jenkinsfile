pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                script {
                    try {
                        // Checkout code from SCM
                        checkout scm
                    } catch (Exception e) {
                        error "Failed to checkout SCM: ${e.getMessage()}"
                    }
                }
            }
        }
        
        stage('Send File to HTTP Server') {
            steps {
                script {
                    try {
                        // Path to the file you want to send
                        def filePath = '/home/ajay-test/server.c'
                        def httpServerUrl = 'http://localhost:8080/home/ajay-test/new'

                        // Check if file exists
                        if (fileExists(filePath)) {
                            // Use curl to send the file to the HTTP server
                            def curlCommand = "curl -X POST ${httpServerUrl} -H 'Content-Type: application/json' --data-binary @${filePath}"
                            
                            // Execute the curl command
                            def response = sh(script: curlCommand, returnStdout: true).trim()
                            
                            // Print response for debugging
                            echo "Response: ${response}"
                        } else {
                            error "File does not exist: ${filePath}"
                        }
                    } catch (Exception e) {
                        error "Failed to send file to HTTP server: ${e.getMessage()}"
                    }
                }
            }
        }
    }
    
    post {
        always {
            // Clean up workspace
            deleteDir()
        }
    }
}

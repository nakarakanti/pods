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
                        def httpServerUrl = 'http://localhost:8081/home/ajay-test/http/server'

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
        success {
            script {
                // Send email notification upon successful completion
                emailext(
                    to: 'ajay.nakarakanti@gmail.com',
                    subject: "Jenkins Build Successful: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                    body: "The build ${env.JOB_NAME} #${env.BUILD_NUMBER} has been successful. The file has been uploaded to the HTTP server.",
                    attachLog: true
                )
            }
        }
        failure {
            script {
                // Optional: Send email notification upon failure
                emailext(
                    to: 'ajay.nakarakanti@gmail.com',
                    subject: "Jenkins Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                    body: "The build ${env.JOB_NAME} #${env.BUILD_NUMBER} has failed. Please check the build log for details.",
                    attachLog: true
                )
            }
        }
    }
}

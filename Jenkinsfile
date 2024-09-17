pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                // Checkout code from SCM
                checkout scm
            }
        }
        
        stage('Send File to HTTP Server') {
            steps {
                script {
                    // Path to the file you want to send
                    def filePath = '/home/ajay-test/server.c'
                    def httpServerUrl = 'http://localhost:8080/your-endpoint'

                    // Read file content
                    def fileContent = readFile(filePath)

                    // Send file content to HTTP server
                    def response = httpRequest(
                        acceptType: 'APPLICATION_JSON',
                        contentType: 'APPLICATION_JSON',
                        httpMode: 'POST',
                        url: httpServerUrl,
                        requestBody: fileContent
                    )

                    // Print response for debugging
                    echo "Response: ${response}"
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

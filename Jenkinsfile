pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Create a ZIP file
                sh 'zip -r myfile.zip /home/ajay-test/http/server/'
            }
        }
        stage('Upload') {
            steps {
                script {
                    def zipFile = 'myfile.zip'
                    def serverUrl = 'http://localhost:8081/home/ajay-test/http'
                    
                    // Debugging: List files to confirm the ZIP file exists
                    sh "ls -l ${zipFile}"
                    
                    // Upload the file
                    sh "curl -X POST -F 'file=@${zipFile}' '${serverUrl}' || { echo 'Upload failed'; exit 1; }"
                }
            }
        }
    }
}

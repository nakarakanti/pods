pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Your build steps here
                sh '''cd $Build_path
                echo "Build is prepared and placed at $Build_path"'''
            }
        }
        stage('Deploy') {
            steps {
                script {
                    def filePath = '/home/ajaytest/Downloads/bzImage-initramfs--6.1-r0-dell-qemux86_64-20240312151614.bin'
                    def targetUrl = 'http://localhost:8080/upload'
                    
                    // Send the file using HTTP PUT
                    sh """
                    curl -X PUT --data-binary "@${filePath}" ${targetUrl}
                    """
                }
            }
        }
    }
}

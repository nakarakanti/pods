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
                    def filePath = '/home/ajaytest/Downloads/*.bin'
                    def targetUrl = 'http://100.105.243.57:8080/home/root'
                    
                    // Send the file using HTTP PUT
                    sh """
                    curl -X PUT --data-binary "@${filePath}" ${targetUrl}
                    """
                }
            }
        }
    }
}

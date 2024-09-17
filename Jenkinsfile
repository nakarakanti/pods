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
                    def filePath = '/home/ajay-test/server.c'
                    def targetUrl = 'http://localhost/upload'

                    // Send the file using HTTP PUT
                    sh """
                    curl -X POST http://localhost:8081/upload \
                     -H "Authorization: Bearer your_token" \
                     -F "file=@/home/ajay-test/server.c"

                    """
                }
            }
        }
    }
}

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
                    // Example for SCP (Secure Copy Protocol)
                    sh '''
                    scp /home/ajaytest/Downloads/*.bin root@100.105.243.57:/home/root/
                    '''
                }
            }
        }
    }
}

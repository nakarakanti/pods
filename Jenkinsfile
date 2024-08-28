pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Your build steps here
                sh 'echo Build is prepared and placed at '
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Example for SCP (Secure Copy Protocol)
                    sh '''
                    scp /home/ajaytest/Downloads/Test.txt root@100.105.243.57:/home/root/
                    '''
                }
            }
        }
    }
}

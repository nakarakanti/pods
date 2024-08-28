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
                    scp -i /path/to/ssh-key -o StrictHostKeyChecking=no \
                       /home/ajaytest/Downloads/bzImage-initramfs--6.1-r0-dell-qemux86_64-20240312151614.bin root@100.105.243.57:/home/root/
                    '''
                }
            }
        }
    }
}

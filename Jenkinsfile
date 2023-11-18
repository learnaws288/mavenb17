pipeline {
   agent any
   environment{
        BUILD_SERVER_IP='ubuntu@65.0.180.13'
    }
    stages {
        stage('SCM') {
            steps {
             git "https://github.com/learnaws288/mavenb17.git"
        }
    }
   stage('package') {
            steps {
                script{
                sshagent(['QA']) {
                    echo "Packaging the code on new slave"
                    sh "scp -o StrictHostKeyChecking=no server-config.sh ${BUILD_SERVER_IP}:/home/ubuntu"
                    sh "ssh -o StrictHostKeyChecking=no ${BUILD_SERVER_IP} 'bash ~/server-config.sh'"
                }     
            }           
        }
        }
}
}

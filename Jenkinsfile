pipeline {
 
    agent any
   
    stages {
        stage('SCM') {
            steps {
                git 'https://github.com/learnaws288/mavenb17.git'
            }         
}
       
        stage('Build by Maven Package') {
            steps {
                sh 'mvn clean package'
            }
        }
        
          stage('Build Docker OWN image') {
            steps {
                sh "sudo docker build -t learndevops16/app:${BUILD_ID} ."

            }
           
        }
          stage('docker push ') {

    steps {
    withCredentials([string(credentialsId: 'DOCKER_HUB_PWD', variable: 'DOCKER_HUB_PASS_CODE')])  {
    // some block
        sh "sudo docker login -u learndevops16 -p $DOCKER_HUB_PASS_CODE"
    }
    sh "sudo docker push learndevops16/app:${BUILD_ID}"

}
}       
       stage('Deploy webAPP in Prod Env') {
steps {
sshagent(['QA']) {
    sh "ssh -o StrictHostKeyChecking=no ubuntu@ 65.2.131.81  sudo  kubectl delete deployment  myjavawebapp" 
sh "ssh -o StrictHostKeyChecking=no ubuntu@13.234.113.231   sudo kubectl create deployment myjavawebapp --image=learndevops16/app:${BUILD_ID}"
sh "ssh ubuntu@13.234.113.231   sudo wget https://raw.githubusercontent.com/learnasws16161616/maven/master/webappsvc.yml"
sh "ssh ubuntu@13.234.113.231   sudo kubectl apply -f webappsvc.yml"
}
}
}
    }
}

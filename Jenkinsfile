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
                sh "sudo docker build -t learndevops16/tomcatapp:${BUILD_ID} ."

            }
           
        }
    stage('docker push ') {

steps {
   withCredentials([string(credentialsId: 'DOCKER_HUB_PWD1', variable: 'DOCKER_HUB_PASS_CODE')])  {
    // some block
    sh "sudo docker login -u learndevops16 -p $DOCKER_HUB_PASS_CODE"
}
 sh "sudo docker push learndevops16/tomcatapp:${BUILD_ID}"

}
}       

stage('Deploy to docker Env') {
steps {
sshagent(['QA']) {
    sh "ssh -o StrictHostKeyChecking=no ubuntu@3.110.106.99  sudo docker rm -f app1" 
  sh "ssh -o StrictHostKeyChecking=no ubuntu@3.110.106.99  sudo docker run -itd --name app1 -p 8080:8080 learndevops16/tomcatapp:${BUILD_ID}" 
}
}
}
stage('Deploy webAPP in Prod Env') {
steps {
sshagent(['QA']) {
    
sh "ssh -o StrictHostKeyChecking=no ubuntu@ 65.2.131.81  sudo  kubectl delete deployment  myjavawebapp" 
sh "ssh -o StrictHostKeyChecking=no ubuntu@65.2.131.81   sudo kubectl create deployment myjavawebapp --image=learndevops16/tomcatapp:${BUILD_ID}"
sh "ssh ubuntu@65.2.131.81   sudo wget https://raw.githubusercontent.com/learnasws16161616/maven/master/webappsvc.yml"
sh "ssh ubuntu@65.2.131.81   sudo kubectl apply -f webappsvc.yml"
}
}
}
    }
}

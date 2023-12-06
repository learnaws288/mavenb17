pipeline {
    agent { label 'java' } 
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
    }
}

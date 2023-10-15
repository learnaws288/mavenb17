pipeline {
    agent { label 'java' }
    
    stages {
        stage('SCM Clone') {
            steps {
         //  git branch: 'main', credentialsId: 'dfe5f943-0d46-4182-9f7b-f360c2f23867', url: 'https://gitlab.com/learnaws288/flipkart-updated.git'
           git 'https://github.com/learnaws288/mavenb17.git'
            }
        }
        stage('Build the project') {
            steps {
         //  git branch: 'main', credentialsId: 'dfe5f943-0d46-4182-9f7b-f360c2f23867', url: 'https://gitlab.com/learnaws288/flipkart-updated.git'
           sh 'mvn clean package'
            }
        }
    }
}
        
     

pipeline {
   agent any
    stages {
        stage('SCM') {
            steps {
             git "https://github.com/learnaws288/mavenb17.git"
        }
    }
     stage('Build') {
            steps {
             sh "mvn clean package"
        }
    }
}
}

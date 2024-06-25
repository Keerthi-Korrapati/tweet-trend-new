def registry = 'https://keerthi01.jfrog.io/'
pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.8/bin:$PATH"
}
    stages {
        stage("build"){
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Sonarqube analysis') {
            environment {
             scannerHome = tool 'keerthi-sonar-scanner' // which is defind jenkins tools 
            }
            steps{
            withSonarQubeEnv('keerthi-sonarqube-server') { // which is defined in jenkins system
                sh "${scannerHome}/bin/sonar-scanner"
            }
            }
        }   
       
    }   

    }

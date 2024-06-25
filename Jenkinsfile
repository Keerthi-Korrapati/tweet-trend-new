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
            tools {
                jdk 'java-11' // Use the JDK 11 tool configured in Jenkins
            }
            steps {
                sh 'mvn clean deploy'
            }
        }
        stage('Sonarqube analysis') {
            tools {
                jdk 'java-17' // Use the JDK 11 tool configured in Jenkins
            }
            environment {
             scannerHome = tool 'keerthi-sonar-scanner' // which is defined jenkins tools 
            }
            steps{
            withSonarQubeEnv('keerthi-sonarqube-server') { // which is defined in jenkins system
                sh "${scannerHome}/bin/sonar-scanner"
            }
            }
        }
    }   
}

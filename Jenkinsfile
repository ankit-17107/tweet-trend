pipeline {
    agent {
        node {
            label 'maven'
        }
    }

environment {
    PATH = "/opt/apache-maven-3.9.2/bin:$PATH"
}    

    stages {
        stage('build') {
            steps {
                sh 'mvn clean deploy'
            }
        }

        stage('SonarQube analysis'){
            environment{
                scannerHome= tool 'sonarqube-server'
            }
            steps{
            withSonarQubeEnv('sonarqube-server'){
                sh "${scannerHome}/bin/sonar-scanner -X"
            }
            }
        }
    }
}

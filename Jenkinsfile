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

        stage('SonarQube analysis') {
            environment {
                scannerHome = tool name: 'SonarQubeScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
            }
            steps {
                withSonarQubeEnv('sonarqube-server') {  // Updated to match the name in your configuration
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}


// pipeline {
//     agent {
//         node {
//             label 'maven'
//         }
//     }

// environment {
//     PATH = "/opt/apache-maven-3.9.2/bin:$PATH"
// }    

//     stages {
//         stage('build') {
//             steps {
//                 sh 'mvn clean deploy'
//             }
//         }

//         stage('SonarQube analysis'){
//             environment{
//                 scannerHome= tool 'ankit17107-sonar-scanner'
//             }
//             steps{
//             withSonarQubeEnv('ankit17107-sonar-scanner'){
//                 sh "${scannerHome}/bin/sonar-scanner"
//             }
//             }
//         }
//     }
// }

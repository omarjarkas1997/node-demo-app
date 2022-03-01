
pipeline {
    agent any

    stages {
        // stage("SCA") {
        //     steps {
        //     dependencyCheck additionalArguments: '--scan="/"', odcInstallation: 'OWASP-Dependency-Check'
        //     dependencyCheckPublisher pattern: 'target/dependency-check-report.xml'
        //     }
        // }
        stage('Scan') {
            steps {
                withSonarQubeEnv(installationName: 'sq1') {
                    sh 'mvn sonar:sonar'
                    sh 'cat target/sonar/report-task.txt'
                }
            }
        }
        stage("build") {
            steps {
                echo "Building the application"
            }
        }
        
        stage("test") {
            steps {
                echo "Testing the application"
            }
        }
        
        stage("deploy") {
            steps {
                echo "Deloying the application"
            }
        }
    }
}


pipeline {
    agent any

    stages {
        // stage("SCA") {
        //     steps {
        //     sh('mkdir -p build/owasp')
        //     dependencyCheck additionalArguments: '--project node-demo-app --scan ./ --disableYarnAudit --out build/owasp/dependency-check-report.xml --format XML', odcInstallation: 'OWASP-Dependency-Check'
        //     dependencyCheckPublisher pattern: 'build/owasp/dependency-check-report.xml'
        //     }
        // }
        stage('Scan') {
            steps {
                withSonarQubeEnv(credentialsId: '0686b948-3ea3-4c84-aaf6-6a207a0c682d', installationName: 'sq1') {
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

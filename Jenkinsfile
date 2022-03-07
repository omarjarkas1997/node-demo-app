
pipeline {
    agent any

    stages {
        stage("SCA") {
            steps {
            sh(`mkdir -p build/owasp`)
            dependencyCheck additionalArguments: '--project node-demo-app --scan ./ --disableYarnAudit --out build/owasp/dependency-check-report.xml --format XML', odcInstallation: 'OWASP-Dependency-Check'
            dependencyCheckPublisher pattern: 'build/owasp/dependency-check-report.xml'
            }
        }
        // stage('Scan') {
        //     steps {
        //         withSonarQubeEnv(credentialsId: '6b3f37ca-db72-4c46-a9d4-b2cf3d562d31', installationName: 'sq1') {
        //             sh 'mvn sonar:sonar'
        //         }
        //     }   
        // }
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

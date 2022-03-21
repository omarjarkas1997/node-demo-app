
pipeline {
    agent any
    tools {
        maven '3.8.1'
    }

    stages {
        stage("SCA") {
            steps {
            sh('mkdir -p build/owasp')
            dependencyCheck additionalArguments: '--project node-demo-app --scan ./ --disableYarnAudit --out build/owasp/dependency-check-report.xml --format XML', odcInstallation: 'OWASP-Dependency-Check'
            dependencyCheckPublisher pattern: 'build/owasp/dependency-check-report.xml'
            }
        }
        stage('SAST') {
            steps {
                withSonarQubeEnv(credentialsId: 'jenkins-sast', installationName: 'sq1') {
                    sh 'mvn sonar:sonar'
                    sh 'cat target/sonar/report-task.txt'
                }
            }   
        }
        stage("DAST") {
            steps {
                "docker run --network demo-network -i owasp/zap2docker-stable"+ 
								"zap-cli quick-scan --spider --self-contained --recursive"+
								"--start-options '-config api.disablekey=true'"+
								"http://10.89.114.248:3000 -l Low"
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


pipeline {
    agent any
    tools {
        maven '3.8.1'
    }

    stages {
        stage("SCA") {
            steps {
            // sh('mkdir -p build/owasp')
            // dependencyCheck additionalArguments: '--scan . --disableYarnAudit --format HTML', odcInstallation: 'OWASP-Dependency-Check'
            // // dependencyCheckPublisher pattern: 'build/owasp/dependency-check-report.html'
            sh 'mvn dependency-check:check'
            dependencyCheckPublisher pattern: 'target/dependency-check-report.xml' 
            }
        }
        stage('SAST') {
            steps {
                withSonarQubeEnv(credentialsId: 'jenkins-sonarqube', installationName: 'sq1') {
                    sh 'mvn sonar:sonar'
                    sh 'cat target/sonar/report-task.txt'
                }
            }   
        }
        // stage("DAST") {
        //     steps {
        //         "sudo apt-get update"
        //         "docker run --network demo-network -i owasp/zap2docker-stable"+ 
		// 						"zap-cli quick-scan --spider --self-contained --recursive"+
		// 						"--start-options '-config api.disablekey=true'"+
		// 						"http://172.16.11.110:3000 -l Low"
        //     }
        // }
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


pipeline {
    agent any

    stages {
	stage("SCA") {
	    steps {
		dependencyCheck additionalArguments: '--scan="/"', odcInstallation: 'OWASP-Dependency-Check'
        dependencyCheckPublisher pattern: 'target/dependency-check-report.xml'
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

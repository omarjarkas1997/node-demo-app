
pipeline {
    agent any

    stages {
	stage("") {
	    steps {
		sh 'chmod +x owasp-dependency-check.sh'
		sh 'bash owasp-dependency-check.sh'

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


pipeline {
    agent any

    stages {
	stage("") {
	    steps {
		sh 'rm owasp* || true'
	    	sh 'wget https://raw.githubusercontent.com/omarjarkas1997/node-demo-app/main/owasp-dependency-check.sh'
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

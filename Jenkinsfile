pipeline {
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install --verbose'
		sh 'npm audit'
            }
        }
	stage('test') {
	    steps {
		sh './jenkins/scripts/test.sh'
	    }
	}
    }
}

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
            }
        }
	stage('test') {
	    steps {
		sh './jenkins/script/test.sh'
	    }
	}
    }
}

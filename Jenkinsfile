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
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
                input message: 'Test berhasil, Anda yakin untuk lanjut ke tahap deployment? (Klik "Proceed" untuk melanjutkan)'
            }
        }
        stage('Deploy') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                sleep(time: 2, unit: 'MINUTES')
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}

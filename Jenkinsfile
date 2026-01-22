pipeline {
    agent {
        docker {
            image 'node:18-alpine' 
            args '--cache .npm' 
        }
    }
    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm ci'
            }
        }
    }
}

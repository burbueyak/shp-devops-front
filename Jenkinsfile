pipeline {
    agent {
        docker { image 'node:18-alpine' }
    }
    stages {
        stage('Install') {
            steps { sh 'npm ci' }
        }
        stage('Build') {
            steps { 
                sh '''
                    npm run build --if-present
                    
                    # Альтернативная команда, если build не сработал
                    if [ ! -d "dist" ] && [ ! -d "build" ]; then
                        echo "Trying alternative build commands..."
                        npm run prod --if-present || npm run compile --if-present
                    fi
                '''
            }
        }
    }
    post {
        success {
            sh 'ls -la dist/ || ls -la build/ || echo "No build directory found"'
        }
    }
}

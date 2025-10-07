pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Test Build') {
            steps {
                sh 'echo "Hello Jenkins"'
                sh 'pwd'
                sh 'ls -la'
            }
        }
    }
}

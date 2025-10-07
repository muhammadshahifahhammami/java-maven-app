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

pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'echo "Pipeline bekerja!"'
            }
        }
    }
}

pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn --version'
                sh 'mvn clean compile -DskipTests'
            }
        }
    }
}

pipeline {
    agent any

    tools {
        maven 'maven-3.9'
        jdk 'jdk-17'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
    }
}

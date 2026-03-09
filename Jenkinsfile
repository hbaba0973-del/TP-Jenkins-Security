pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning repository...'
                git 'https://github.com/ton-username/TP-Jenkins-Security.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                sh 'pip install -r requirements.txt'
            }
        }
        
        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh 'pytest'
            }
        }
        
        stage('SCA Scan') {
            steps {
                echo 'Running OWASP Dependency-Check...'
                sh 'dependency-check.sh --project "TP-Jenkins" --scan . --format HTML'
            }
        }
    }
    
    post {
        failure {
            echo 'Build failed due to errors or vulnerabilities'
        }
    }
}

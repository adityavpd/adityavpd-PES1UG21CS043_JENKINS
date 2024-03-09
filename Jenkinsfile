pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                branches: [[name: '*/main']],
                userRemoteConfigs: [[url: 'https://github.com/AdityaArakere/adityavpd-PES1UG21CS043_JENKINS.git']]])
            }
        }
        
        stage('Build') {
            steps {
                build 'PES1UG21CS043-1'
                sh 'g++ main/pipeline.cpp -o output'
            }
        }
        
        stage('Test') {
            steps {
                sh './output'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'deploy'
            }
        }
    }
    
    post {
        failure {
            error 'Pipeline failed'
        }
    }
}

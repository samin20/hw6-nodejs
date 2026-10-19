pipeline {
    agent any

    tools {
        nodejs 'NodeJS-24'
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build Artifact') {
            steps {
                sh 'tar -czf nodejs-app.tar.gz --exclude=node_modules --exclude=.git --exclude=nodejs-app.tar.gz .'
                archiveArtifacts artifacts: 'nodejs-app.tar.gz', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
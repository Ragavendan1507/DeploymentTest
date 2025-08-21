pipeline {
    agent any
     tools {
        nodejs "NodeJS" 
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Ragavendan1507/DeploymentTest.git', branch: 'master'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
               sh 'firebase deploy'
               
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished successfully 🎉'
        }
        failure {
            echo 'Pipeline failed ❌'
        }
    }
}

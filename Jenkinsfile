pipeline {
    agent any

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

        stage('Test') {
            steps {
                sh 'npm run test' 
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy step here (e.g., copy build to server)'
               
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

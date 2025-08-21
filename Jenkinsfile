pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/your-username/your-vite-project.git', branch: 'main'
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
                sh 'npm run test'  // optional, only if you have tests
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy step here (e.g., copy build to server)'
                // Example: sh 'scp -r dist/* user@server:/var/www/html/'
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

pipeline {
    agent any

    tools {
        nodejs "node js"
    }

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('DOCKER_HUB_TOKEN')
        FIREBASE_TOKEN = credentials('FIREBASE_TOKEN')
        DOCKER_IMAGE = 'ragav1526/vite-app:latest'
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

        stage('Docker Build & Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: "${DOCKER_HUB_CREDENTIALS}", usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh '''
                        echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                        docker build -t $DOCKER_IMAGE .
                        docker push $DOCKER_IMAGE
                    '''
                }
            }
        }

        stage('Firebase Deploy') {
            steps {
                sh '''
                    npm install -g firebase-tools
                    firebase deploy --token $FIREBASE_TOKEN
                '''
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

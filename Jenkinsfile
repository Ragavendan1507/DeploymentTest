pipeline {
    agent any
     tools {
        nodejs "node js" 
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

        stage('Build') {stage('Deploy') {
    steps {
        withCredentials([string(credentialsId: 'FIREBASE_TOKEN', variable: 'FIREBASE_TOKEN')]) {
            sh 'npx firebase deploy --token "$FIREBASE_TOKEN"'
        }
    }
}

            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy') {
    steps {
        withCredentials([string(credentialsId: 'FIREBASE_TOKEN', variable: 'FIREBASE_TOKEN')]) {
            sh 'npx firebase deploy --token $FIREBASE_TOKEN'
        }
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

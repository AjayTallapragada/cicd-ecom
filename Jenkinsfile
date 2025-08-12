pipeline {
    agent any

    tools {
        nodejs 'node16' // Change this to whatever NodeJS name is in Jenkins Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/AjayTallapragada/cicd-ecom.git'
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

        stage('Deploy to Nginx') {
            steps {
                sh 'sudo cp -r build/* /var/www/html/'
            }
        }
    }
}

pipeline {
    agent any

    tools {
        nodejs "node16" // Name from NodeJS plugin configuration
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
                sh 'sudo rm -rf /var/www/html/*'
                sh 'sudo cp -r dist/* /var/www/html/'
                sh 'sudo systemctl restart nginx'
            }
        }
    }
}

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
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Deploy to IIS') {
            steps {
                // Delete old files
                bat 'del /Q C:\\inetpub\\wwwroot\\*'
                
                // Copy new build to IIS folder
                bat 'xcopy dist C:\\inetpub\\wwwroot /E /H /C /I'
            }
        }
    }
}

pipeline {
    agent any

    environment {
        NODEJS_HOME = tool 'nodejs-lts'
        PATH = "${NODEJS_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/ReubenDickson/mern-stack-deploy-backend.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deployment') {
            steps {
                sh 'pm2 restart app'
            }
        }
    }
}

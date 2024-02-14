pipeline {
    agent any

    stages {
        stage('Use Node.js from package.json') {
            steps {
                echo 'Setting up NVM...'
                script {
                    def nvmHome = tool name: 'NVM', type: 'hudson.plugins.nvm.NvmInstallation'
                    env.PATH = "${nvmHome}/bin:${env.PATH}"
                    sh 'nvm use $(jq -r ".engines.node" package.json) || echo "Failed to use Node.js version"'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'npm run lint'
                sh 'npm test'
                sh 'npm run build'
                echo 'Build complete.'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'npm test'
            }
        }

        stage('Deliver') {
            steps {
                echo 'Delivering the application...'
                // Add steps for deployment or delivery
            }
        }
    }

    post {
        failure {
            echo 'Deployment failed'
        }
    }
}

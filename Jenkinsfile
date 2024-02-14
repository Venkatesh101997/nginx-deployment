pipeline {
    agent any

    environment {
        CI = 'true'
        NVM_DIR = "$HOME/.nvm"
    }

    tools {
        nodejs 'node' // Assuming you have a NodeJS tool installation named 'node' in Jenkins
        git 'git' // Assuming you have a Git tool installation named 'git' in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                checkout scm
                echo 'Code checkout complete.'
            }
        }

        stage('Use Node.js from package.json') {
            steps {
                echo 'Setting up NVM...'
                sh '''
                    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                '''
                sh 'nvm use $(jq -r ".engines.node" package.json)'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing npm dependencies...'
                sh 'npm install'
                echo 'npm install complete.'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the React application...'
                sh 'npm run build'
                echo 'Build complete.'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing..'
                sh '''
                    echo "doing test stuff.."
                '''
            }
        }

        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                    echo "doing delivery stuff.."
                '''
            }
        }

        stage('Deploy to Nginx') {
            steps {
                echo 'Deploying to Nginx...'
                // Adjust the paths accordingly
                sh 'rsync -av --delete --exclude="node_modules" ./ /usr/share/nginx/'
                echo 'Deployment complete.'
            }
        }

        stage('Restart Nginx') {
            steps {
                echo 'Restarting Nginx...'
                sh 'sudo systemctl restart nginx'
                echo 'Nginx restart complete.'
            }
        }
    }

    post {
        success {
            echo 'Deployment successful'
            // Additional success actions or notifications
        }
        unstable {
            echo 'Deployment unstable - check logs'
            // Additional actions for unstable build
        }
        failure {
            echo 'Deployment failed'
            // Additional failure actions or notifications
        }
    }
}

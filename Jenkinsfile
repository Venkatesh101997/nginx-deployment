pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the code from GitHub
                git 'https://github.com/Venkatesh101997/nginx-deployment.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install dependencies using npm for Node.js projects
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                // Add build steps if needed
            }
        }

        stage('Deploy to Nginx') {
            steps {
                // Copy files to Nginx path (adjust paths accordingly)
                sh 'rsync -av --delete ./ /usr/share/nginx/'
            }
        }

        stage('Restart Nginx') {
            steps {
                // Restart Nginx if needed
                sh 'sudo systemctl restart nginx'
            }
        }
    }

    post {
        success {
            // Additional success actions or notifications
        }
        failure {
            // Additional failure actions or notifications
        }
    }
}

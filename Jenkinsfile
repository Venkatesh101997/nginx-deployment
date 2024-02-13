pipeline {
    agent any

    environment {
        CI = 'true'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    git url: 'https://github.com/Venkatesh101997/nginx-deployment.git', branch: 'main'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    echo 'Building the application'
                    // Add your actual build steps here
                }
            }
        }

        stage('Deploy to Nginx') {
            steps {
                script {
                    // Adjust the paths accordingly
                    sh 'rsync -av --delete --exclude="node_modules" ./ /usr/share/nginx/'
                }
            }
        }

        stage('Restart Nginx') {
            steps {
                script {
                    sh 'sudo systemctl restart nginx'
                }
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

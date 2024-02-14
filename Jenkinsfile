pipeline {
    agent any

    stages {
        stage('Declarative: Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Use Node.js from package.json') {
            steps {
                echo 'Setting up NVM...'
                script {
                    // Define the NodeJS installation name (make sure it matches the one in your Jenkins configuration)
                    def nodejsInstallation = tool name: 'NVM', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
                    env.PATH = "${nodejsInstallation}/bin:${env.PATH}"
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
                    sh 'npm run build'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh 'npm test'
                }
            }
        }

        stage('Deliver') {
            steps {
                // Add steps for delivering your application
                // For example, deploying to a server or packaging the application
            }
        }

        stage('Declarative: Post Actions') {
            steps {
                echo 'Deployment failed'
            }
        }
    }

    post {
        always {
            // Add cleanup steps or notifications that need to be executed regardless of the pipeline result
        }
    }
}

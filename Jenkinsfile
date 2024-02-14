stage('Use Node.js from package.json') {
    steps {
        echo 'Setting up NVM...'
        sh '''
            export NVM_DIR="$HOME/.nvm"
            [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" || echo "Failed to source nvm.sh"
        '''
        sh 'nvm use $(jq -r ".engines.node" package.json) || echo "Failed to use Node.js version"'
    }
}

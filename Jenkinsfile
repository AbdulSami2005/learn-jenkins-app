pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat '''
                    node --version
                    npm --version

                    npm install

                    npm run build
                '''
            }
        }
        stage('Test'){
            steps{
                sh 'test -f build/index.html'
            }
        }
    }
}
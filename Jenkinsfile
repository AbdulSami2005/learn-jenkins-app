pipeline {
    agent any

    stages {
        stage('build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                    // Fix: Overrides the Windows drive syntax with a Linux path format for Docker
                    customWorkspace '/c/ProgramData/Jenkins/.jenkins/workspace/learn-jenkins-app'
                }
            }
            steps {
                // Ensure commands are pushed entirely to the left margin
                sh '''
ls -la
node --version
npm --version
npm ci
npm run build
ls -la
                '''
            }
        }
    }
}

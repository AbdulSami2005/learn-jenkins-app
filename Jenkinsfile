pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                nodejs('Node_latest') { 
                    bat 'npm install'
                    bat 'npm run build'
                }
            }
        }
        
       stage('Test') {
            steps {
                nodejs('Node_latest') {
                    // Uses Windows 'bat' and gracefully exits if no test files exist yet
                    bat 'npm test -- --passWithNoTests --watchAll=false'
                }
            }
        }

        stage('Deliver') {
            steps {
                // Safely remove any existing container running your app
                bat 'docker stop my-react-app || exit 0'
                bat 'docker rm my-react-app || exit 0'
                
                // Build the application image using your local Docker Desktop
                bat 'docker build -t react-jenkins-app .'
                
                // Run your React app container on port 3000
                bat 'docker run -d --name my-react-app -p 3000:80 react-jenkins-app'
            }
        }


        
    }
}
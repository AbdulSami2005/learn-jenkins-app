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

        stage('Test') {
            steps {
                bat '''
                    if exist build\\index.html (
                        echo Build Successful
                    ) else (
                        echo Build Failed
                        exit /b 1
                    )
                '''
            }
        }

    }
}
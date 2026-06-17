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

                    dir
                '''
            }
        }

        stage('Test') {
            steps {
                bat '''
                    if exist build\\index.html (
                        echo Build Successful
                    ) else (
                        echo Build folder not found
                        dir
                        exit /b 1
                    )
                '''
            }
        }

    }
}
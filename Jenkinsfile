pipeline {
    agent any

    stages {

        stage('Build') {
    steps {
        // This forces Jenkins to use the Node setup we configured in the Tools menu
        nodejs('Node_latest') { 
            bat 'npm install'
            bat 'npm run build'
        }
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
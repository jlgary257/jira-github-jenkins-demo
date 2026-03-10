pipeline {

    agent any

    environment {
        DEPLOY_DIR = 'C:\\jenkins-php-demo-deploy'
    }

    stages {

        stage('Checkout Source') {
            steps {
                checkout scm
            }
        }

        stage('Verify Files') {
            steps {
                bat '''
                if not exist index.php (
                    echo index.php not found
                    exit /b 1
                )
                if not exist health.php (
                    echo health.php not found
                    exit /b 1
                )
                echo Application files verified
                '''
            }
        }

        stage('Deploy Application') {
            steps {
                bat '''
                if not exist "%DEPLOY_DIR%" mkdir "%DEPLOY_DIR%"
                copy /Y index.php "%DEPLOY_DIR%\\index.php"
                copy /Y health.php "%DEPLOY_DIR%\\health.php"
                echo Deployment completed
                '''
            }
        }
    }

}


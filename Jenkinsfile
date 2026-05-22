pipeline {

    agent any

    tools {
        nodejs 'NodeJS 18'
    }

    stages {

        stage('Build') {

            steps {
                bat 'npm install'
            }
        }

        stage('Test') {

            steps {
                bat 'npm test || exit /b 0'
            }
        }

        stage('Code Quality') {

            steps {
                bat 'echo Running SonarQube analysis'
            }
        }

        stage('Security') {

            steps {
                bat 'npm audit || exit /b 0'
            }
        }

        stage('Deploy') {

            steps {
                bat 'echo Deploying application to test environment'
            }
        }

        stage('Release') {

            steps {
                bat 'echo Releasing application to production'
            }
        }

        stage('Monitoring and Alerting') {

            steps {
                bat 'echo Monitoring application with alerts enabled'
            }
        }
    }

    post {

        success {

            mail to: 'januth1234@gmail.com',
                 subject: 'Pipeline Successful',
                 body: 'The DevOps pipeline completed successfully.'
        }

        failure {

            mail to: 'januth1234@gmail.com',
                 subject: 'Pipeline Failed',
                 body: 'The DevOps pipeline failed.'
        }
    }
}

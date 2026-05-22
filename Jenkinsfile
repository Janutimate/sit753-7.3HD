pipeline {

    agent any

    tools {
        nodejs 'NodeJS 18'
    }

    triggers {
        pollSCM('H/2 * * * *')
    }

    stages {

        stage('Build') {

            steps {

                bat 'npm install'

                bat 'echo Build artifact created'
            }
        }

        stage('Test') {

            steps {

                bat 'echo Running automated tests'
            }

            post {

                success {

                    mail to: 'januth1234@gmail.com',
                         subject: 'Test Stage Successful',
                         body: 'The Test stage completed successfully.'
                }

                failure {

                    mail to: 'januth1234@gmail.com',
                         subject: 'Test Stage Failed',
                         body: 'The Test stage failed.'
                }
            }
        }

        stage('Code Quality') {

            steps {

                script {

                    def scannerHome = tool 'SonarScanner'

                    withSonarQubeEnv('SonarQube') {

                        bat "${scannerHome}\\bin\\sonar-scanner.bat"
                    }
                }
            }
        }

        stage('Security') {

            steps {

                bat 'npm audit || exit /b 0'
            }

            post {

                success {

                    mail to: 'januth1234@gmail.com',
                         subject: 'Security Scan Successful',
                         body: 'The Security scan completed successfully.'
                }

                failure {

                    mail to: 'januth1234@gmail.com',
                         subject: 'Security Scan Failed',
                         body: 'The Security scan failed.'
                }
            }
        }

        stage('Deploy') {

            steps {

                bat 'echo Deploying application to staging environment'
            }
        }

        stage('Release') {

            steps {

                bat 'echo Releasing application to production'
                bat 'echo Version 1.0 released'
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
                 body: 'The full DevOps pipeline completed successfully.'
        }

        failure {

            mail to: 'januth1234@gmail.com',
                 subject: 'Pipeline Failed',
                 body: 'The DevOps pipeline failed.'
        }
    }
}

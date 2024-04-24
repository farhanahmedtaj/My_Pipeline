pipeline {
    agent any
    
    environment {
        DIRECTORY_PATH = 'E:\\T1 2024\\Professional Practice'
        TESTING_ENVIRONMENT = 'QA'
        PRODUCTION_ENVIRONMENT = 'Farhan_Ahmed'
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Fetching the source code from the specified directory path'
                echo 'Compiling the code and generating artifacts'
                echo "Initiating build process using Jenkins..."
            }
            post {
                success {
                    echo 'The build succeeded!'
                    mail to: 'farhanahmedtaj@gmail.com', subject: 'Build Successful', body: 'Congratulations! The build was successful.'
                }
                failure {
                    echo 'The build failed!'
                    mail to: 'farhanahmedtaj@gmail.com', subject: 'Build Failed', body: 'Sorry, the build failed.'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests..."
                echo "Running integration tests..."
            }
            post {
                success {
                    echo 'Tests passed!'
                    emailext body: 'Unit and Integration Tests passed successfully!', subject: 'Tests Passed', to:'farhanahmedtaj@gmail.com', attachLog: true, mimeType: 'text/plain' 
                   }
                failure {
                    echo 'Tests failed!'
                    emailext body: 'Unit and Integration Tests failed!', subject: 'Tests Failed', to:'farhanahmedtaj@gmail.com', attachLog: true, mimeType: 'text/html' 
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Analyzing code using static analysis tools..."
            }
            
        }
        stage('Security Scan') {
            steps {
                echo "Conducting security scan using appropriate plugins..."
            }
            post {
                success {
                    echo 'Security scan passed!'
                    emailext body: 'Security scan passed successfully!', subject: 'Security Scan Passed',  to:'farhanahmedtaj@gmail.com', attachLog: true, mimeType: 'text/html'  
                }
                failure {
                    echo 'Security scan failed!'
                    emailext body: 'Security scan failed!', subject: 'Security Scan Failed',  to:'farhanahmedtaj@gmail.com', attachLog: true, mimeType: 'text/html'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying application to staging server..."
            }
            post {
                success {
                    echo 'Deployment to staging was successful!'
                    mail to: 'farhanahmedtaj@gmail.com', subject: 'Deployment to Staging Successful', body: 'The deployment to staging was successful!'
                }
                failure {
                    echo 'Deployment to staging failed!'
                    mail to: 'farhanahmedtaj@gmail.com', subject: 'Deployment to Staging Failed', body: 'The deployment to staging failed!'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging environment..."
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying application to production server..."
            }
            post {
                success {
                    echo 'Deployment to production was successful!'
                    mail to: 'farhanahmedtaj@gmail.com', subject: 'Deployment to Production Successful', body: 'The deployment to production was successful!'
                }
                failure {
                    echo 'Deployment to production failed!'
                    mail to: 'farhanahmedtaj@gmail.com', subject: 'Deployment to Production Failed', body: 'The deployment to production failed!'
                }
            }
        }
    }
    
    post {
        always {
            echo 'This will always execute'
        }
        success {
            echo 'This will run only if the build is successful'
            mail to: 'farhanahmedtaj@gmail.com', subject: '${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} - Successful', body: 'Congratulations! Your project has passed all stages successfully.'
        }
        failure {
            echo 'This will run only if the build fails'
            mail to: 'farhanahmedtaj@gmail.com', subject: '${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} - Failed', body: 'We are sorry, your build has failed.'
        }
        unstable {
            echo 'This will run only if the build is unstable'
            mail to: 'farhanahmedtaj1@gmail.com', subject: '$JOB_NAME - Build # $BUILD_NUMBER - Unstable', body: 'Your build is unstable.'
        }
        changed {
            echo 'This will run only if the build status changes'
            mail to: 'farhanahmedtaj@gmail.com', subject: '$JOB_NAME - Build # $BUILD_NUMBER - Status Changed', body: 'The build status has changed.'
        }
    }
}

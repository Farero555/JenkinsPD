pipeline {
    agent any
    
    stages {
        stage('Cleanup') {
            steps {
                echo 'Cleaning up the workspace...'
                bat 'if exist python-greetings rmdir /s /q python-greetings'
            }
        }
        stage('install-pip-deps') {
            steps {
                echo 'Cloning the repository...'
                bat 'git clone https://github.com/mtararujs/python-greetings.git'
                echo 'Repository cloned successfully.'

                echo 'Installing Python dependencies from requirements.txt...'
                bat 'pip3 install -r python-greetings/requirements.txt'
                bat 'if exist python-greetings rmdir /s /q python-greetings'
            }
        }
        stage('deploy-to-dev') {
            steps {
                echo 'Deploying application to the Development environment...'
                bat 'git clone https://github.com/mtararujs/python-greetings.git'
                bat 'pm2 delete greetings-app-dev || EXIT /B 0'
                bat 'pm2 start python-greetings/app.py --name greetings-app-dev -- --port 7001'
            }
        }
        stage('tests-on-dev') {
            steps {
                echo 'Executing tests in the Development environment...'
            }
        }
        stage('deploy-to-staging') {
            steps {
                echo 'Deploying application to the Staging environment...'
            }
        }
        stage('tests-on-staging') {
            steps {
                echo 'Executing tests in the Staging environment...'
            }
        }
        stage('deploy-to-preprod') {
            steps {
                echo 'Deploying application to the Pre-Production environment...'
            }
        }
        stage('tests-on-preprod') {
            steps {
                echo 'Executing tests in the Pre-Production environment...'
            }
        }
        stage('deploy-to-prod') {
            steps {
                echo 'Deploying application to the Production environment...'
            }
        }
        stage('tests-on-prod') {
            steps {
                echo 'Executing tests in the Production environment...'
            }
        }
    }
}

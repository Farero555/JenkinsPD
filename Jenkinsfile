pipeline {
    agent any
    
    stages {
        // stage('Clean Workspace') {
        //     steps {
        //         cleanWs()
        //     }
        // }
        stage('install-pip-deps') {
            steps {
                echo 'Cloning the repository...'
                git(
                    url: "https://github.com/mtararujs/python-greetings.git",
                    branch: "main"
                )
                bat "git checkout 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51"
                bat 'dir'
                echo 'Repository cloned successfully.'

                echo 'Installing Python dependencies from requirements.txt...'
                bat 'pip3 install -r requirements.txt'
            }
        }
        stage('deploy-to-dev') {
            steps {
                echo 'Deploying application to the Development environment...'
                git(
                    url: "https://github.com/mtararujs/python-greetings.git",
                    branch: "main"
                )
                bat "git checkout 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51"
                bat 'pm2 delete greetings-app-dev || EXIT /B 0'
                bat 'pm2 start app.py --name greetings-app-dev -- --port 7001'
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

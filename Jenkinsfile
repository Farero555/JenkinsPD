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
                git(
                    url: "https://github.com/mtararujs/course-js-api-framework.git",
                    branch: "main"
                )
                bat "npm install"
                bat "npm run greetings greetings_dev"
            }
        }
        stage('deploy-to-staging') {
            steps {
                echo 'Deploying application to the Staging environment...'
                git(
                    url: "https://github.com/mtararujs/python-greetings.git",
                    branch: "main"
                )
                bat "git checkout 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51"
                bat 'pm2 delete greetings-app-staging || EXIT /B 0'
                bat 'pm2 start app.py --name greetings-app-staging -- --port 7002'
            }
        }
        stage('tests-on-staging') {
            steps {
                echo 'Executing tests in the Staging environment...'
                bat "npm install"
                bat "npm run greetings greetings_staging"
            }
        }
        stage('deploy-to-preprod') {
            steps {
                echo 'Deploying application to the Pre-Production environment...'
                git(
                    url: "https://github.com/mtararujs/python-greetings.git",
                    branch: "main"
                )
                bat "git checkout 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51"
                bat 'pm2 delete greetings-app-preprod || EXIT /B 0'
                bat 'pm2 start app.py --name greetings-app-preprod -- --port 7003'
            }
        }
        stage('tests-on-preprod') {
            steps {
                echo 'Executing tests in the Pre-Production environment...'
                bat "npm install"
                bat "npm run greetings greetings_preprod"
            }
        }
        stage('deploy-to-prod') {
            steps {
                echo 'Deploying application to the Production environment...'
                git(
                    url: "https://github.com/mtararujs/python-greetings.git",
                    branch: "main"
                )
                bat "git checkout 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51"
                bat 'pm2 delete greetings-app-prod || EXIT /B 0'
                bat 'pm2 start app.py --name greetings-app-prod -- --port 7004'
            }
        }
        stage('tests-on-prod') {
            steps {
                echo 'Executing tests in the Production environment...'
                bat "npm install"
                bat "npm run greetings greetings_prod"
            }
        }
    }
}

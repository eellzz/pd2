pipeline {
    agent any
    stages {
        stage('install-pip-deps') {
            steps {
                echo 'installing pip deps'
                dir("installpipdeps") {
                    git(
                        url: "https://github.com/mtararujs/python-greetings.git",
                        branch: "main",
                        changelog: true,
                        poll: true
                    )
                    script {
                        bat 'dir'
                        bat 'C:\\Users\\eliza\\anaconda3\\python.exe -m pip install -r requirements.txt'
                }
                }
            }
        }
        stage('deploy-to-dev') {
            steps {
                echo 'deploying on dev'
                dir("deploytodev") {
                    git(
                        url: "https://github.com/mtararujs/python-greetings.git",
                        branch: "main",
                        changelog: true,
                        poll: true
                    )
                    script {
                        bat 'npm install -g pm2'
                        //bat 'C:\\Users\\eliza\\AppData\\Roaming\\npm\\pm2 delete greetings-app-dev & set "errorlevel=0"'
                        bat 'C:\\Users\\eliza\\AppData\\Roaming\\npm\\pm2 start app.py --interpreter "C:\\Users\\eliza\\anaconda3\\python.exe" --name greetings-app-dev -- --port 7001'
                }
                }
            }
        }
        stage('tests-on-dev') {
            steps {
                echo 'testing on dev'
                dir("testsondev") {
                    git(
                        url: "https://github.com/mtararujs/course-js-api-framework.git",
                        branch: "main",
                        changelog: true,
                        poll: true
                    )
                    script {
                        bat 'npm install -g pm2'
                        bat 'npm install -g mocha'
                        bat 'npm run greetings greetings_dev'
                        
                }
                }
            }
        }
        stage('deploy-to-staging') {
            steps {
                echo 'deploying to staging'
            }
        }
        stage('tests-on-staging') {
            steps {
                echo 'testing on staging'
            }
        }
        stage('deploy-to-preprod') {
            steps {
                echo 'deploying to preprod'
            }
        }
        stage('tests-on-preprod') {
            steps {
                echo 'testing on preprod'
            }
        }
        stage('deploy-to-prod') {
            steps {
                echo 'deploying on prod'
            }
        }
        stage('tests-on-prod') {
            steps {
                echo 'testing on prod'
            }
        }
    }
}


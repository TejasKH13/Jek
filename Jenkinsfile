pipeline {
    agent none
    parameters {
                string defaultValue: 'main', description: 'Provide the branch name ', name: 'Branch', trim: true
                booleanParam description: 'Uncheck this actually deploy', name: 'DRY-RUN'
                choice choices: ['Build', 'Test', 'Deploy'], description: 'chose proper option to run', name: 'Enviornment'
                }
            environment {
            BRANCH = "main"
            }


    stages {
        stage('Stage1') {
            agent {
                label 'slave1'
            }
            environment {
                APP = "Frontend"
            }
            steps {
                sh '''
                    echo APP - $APP
                    pwd
                    ls -lt
                    echo "Branch: $Branch
                '''
                echo "${env.BRANCH}"
                echo "${params.}"
            }
        }
        stage('Stage2') {
            agent {
                label 'slave2'
            }
            environment {
                APP_1 = "Backend"
            }
            steps {
                sh '''
                    echo "APP_1 - $APP_1"
                    echo "Enviornment: $Enviornment"
                    hostname
                    hostname -I
                '''

            }
        }
        stage('stage3') {
            agent {
                label 'master'
            }
            steps {
                sh '''
                    echo "all stages are complete successfully"
                '''
            }
        }
    }
}
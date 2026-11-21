pipeline {
    agent none
    parameters {
                string defaultValue: 'main', description: 'Provide the branch name to build or deploy', name: 'Branch', trim: true
                booleanParam description: 'Un-check this to actually deploy', name: 'DRYRUN'
                choice choices: ['Build', 'Test', 'Deploy'], description: 'Select the environment based on the request', name: 'Environment'
            }
            environment {
                        BRANCH = "main"
                    }
    stages {
        stage('Build') {
            environment {
                APP = "Front"
            }
            steps {
                sh '''
                    echo "Running Stage Build"
                    pwd
                    ls -lt
                    uptime
                    echo "App : $APP"
                '''
                echo "Application : ${env.APP}"
                echo "Environment: ${params.Environment}"
            }
        }
        stage('Test') {
            environment {
                Test = "Testing"
            }
            steps {
                sh '''
                    echo "Welcome to testing stage"
                    hostname -I 
                    hostname
                    whoami
                    '''
                echo "test: ${env.Test}"
                echo "RunType: ${params.DRYRUN} "
            }
        }
        stage('DEPOLY') {
            environment {
                Deploy = "Deployment"
            }
            steps {
                sh '''
                    echo "welcome to last stage and all stages will ends here"
                    ls -ld */
                    date
                    echo "Deploy : $Deploy"
                    '''
                echo "Deploy : ${env.Deploy}"
                echo "Branch : ${params.Branch}"
                
            }
        }

    }
}
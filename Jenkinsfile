def stage6Status = ''

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
            agent{
                label 'slave1'
            }
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
            agent {
                label 'slave2'
            }
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
            agent {
                label 'master'
            }
            environment {
                Deploy = "Deployment"
            }
            steps {
                sh '''
                    echo "welcome to last stage and all stages will ends here"
                    ls -l
                    date
                    echo "Deploy : $Deploy"
                    '''
                echo "Deploy : ${env.Deploy}"
                echo "Branch : ${params.Branch}"
                
            }
        }
        stage('Production') {
            agent {
                label 'slave1'
            }
            steps {
                catchError(buildResult: 'SUCCESS' , stageResult: 'FAILURE') {
                    sh '''
                        ls
                     '''
                    }
            }
        }
        stage('Server') {
            agent {
                label 'slave2'
            }
            steps {
                script {
                    try {
                        sh '''
                            exit 1
                         '''
                    } catch(Exception e) {
                        echo "Got an exeption: ${e.message}"
                        currentBuild.result = 'SUCESS'
                    }finally {
                        echo "cleaning up ..."
                    }

                }
            }
        }
        stage('Stage6') {
            agent {
                label 'master'
            }
            steps {
                script {
                    try {
                        sh '''
                            exit 1
                         '''
                        stage6Status = 'SUCCESS'

                        } catch (Exception x) {
                            echo "Caught an exception ${x.message}"
                            stage6Status = 'FAILED'

                        }
                }
                
            }
        }
        stage('stage6') {
            agent {
                label 'slave1'
            }
            when {
                expression {
                    stage6Status == 'SUCCESS'
                }
            }
            steps {
                echo "stage 6 is executed"
            }
        }
        stage('Final') {
            agent {
                label = 'slave2'
            }
            steps {
                echo "final steps is executed"
            }
        }



    }
}
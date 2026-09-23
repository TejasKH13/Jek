pipeline {
    agent any
    options {
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '20')
        disableConcurrentBuilds()
        timeout(time: 10, unit: 'SECONDS')
        retry(2)
        timestamps()
        ansiColor('xterm')
        }


    stages {
        stage('Stage1') {
            steps {
                sh 'pwd'
                checkout scmGit(
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[
                        credentialsId: 'class_git',
                        url: 'https://github.com/TejasKH13/Jek.git'
                    ]]
                )
            }
        }

        stage('STAGE2') {
            parallel {
                stage('sub-stage1') {
                    steps {
                        echo 'running sub stage1'
                        sh '''
                            ls -la
                            pwd
                        '''
                    }
                }

                stage('sub-stage2') {
                    steps {
                        echo 'running sub stage2'
                        sh 'find . -maxdepth 1 -type f'
                    }
                }

                stage('sub-stage3') {
                    steps {
                        echo 'running sub stage3'
                        sh 'whoami'
                    }
                }
            }
        }
    }
}

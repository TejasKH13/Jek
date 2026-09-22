pipeline {
    agent any
    stages {
        stage ('STEPS1') {
            sh 'pwd'
            checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'class_git', url: 'https://github.com/TejasKH13/Jek.git']])
   
        }
        stage ('STEPS2') {
            parallel {
                stage ('sub-stage1') {
                    echo "running sub stage1"
                    sh '''
                        ls -la
                        pwd
                        '''
                }
                stage ('sub-stage2') {
                    echo "runnig sub stage2"
                    sh 'find * -maxdepth 1 -type f'
                }
                stage ('sub-stage3') {
                    echo "running sub stage3"
                    sh 'ls -ld */'
                }
            }

        }
    }
}
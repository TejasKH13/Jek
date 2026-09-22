pipeline {
    agent any
    stages {
        stage ('STAGE1') {
            steps {
                sh 'pwd'
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'class_git', url: 'https://github.com/TejasKH13/Jek.git']])
            }
        }
        stage ('STAGE2') {
            steps {
                sh 'pwd'
                sh 'ls -lrt'
            }
        }
    }
}
pipeline {
    agent any
    stages {
        stage ('STAGE1') {
            steps {
                sh 'pwd'
                git branch: 'main',
                    credentialsId: 'class_git',
                    url: 'https://github.com/TejasKH13/Jek.git'
            }
        }
        stage ('STAGE2') {
            steps {
                sh '''
                    pwd
                    ls -lrt
                    '''
            }
        }
    }

}
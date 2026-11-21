pipeline {
    agent none
    stages {
        stage('Stage1') {
            agent {
                label 'slave1'
            }
            steps {
                sh '''
                    pwd
                    ls -lt
                '''
            }
        }
        stage('Stage2') {
            agent {
                label 'slave2'
            }
            steps {
                sh '''
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
pipeline {
    agent {
        label 'slave1'
    }
    stages {
        stage('Stage1') {
            steps {
                sh '''
                    pwd
                    ls -lt
                '''
            }
        }
        stage('Stage2') {
            steps {
                sh '''
                    hostname
                    hostname -I
                '''
            }
        }
        stage('stage3') {
            steps {
                sh '''
                    echo "all stages are complete successfully"
                '''
            }
        }
    }
}
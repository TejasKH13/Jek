pipeline{
    agent any
    stages{
        stage('Stage1'){
            steps{
                sh 'ls -lt'
            }

        }
        stage('Stage2'){
            steps{
                sh '''
                pwd
                date
                hostnamectl
                '''
            }

        }
        stage('Stage3'){
            steps{
                echo 'building stage 3'
            }

        }
        stage('Stage4'){
            steps{
                sh 'echo this is stage 4'
            }

        }
    }
}
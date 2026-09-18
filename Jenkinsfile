pipeline
{
    agent none
    stages
    {
        stage('STAGE1')
        {
            agent any
            steps
            {
                sh '''
                    ls -lt
                    sleep 5
                '''
            }
        }
        stage('STAGE2')
        {
            agent {
                label 'slave1'
            }
            steps{
                sh '''
                    #!/bin/bash
                    pwd
                    whoami
                '''
            }

        }
        stage ('STAGE3')
        {
            agent{
                label 'slave2'
            }
            steps{
                echo "This is stage 3"

            }
        }
        stage('STAGE4')
        {
            agent any
            steps{
                sh 'echo "this is stage 4"'

            }
        }
    }
}
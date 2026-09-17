pipeline
{
    agent any
    stages
    {
        stage('STAGE1')
        {
            steps
            {
                sh 'ls -lrt'
            }
        }
        stage('STAGE2')
        {
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
            steps{
                echo "This is stage 3"

            }
        }
        stage('STAGE4')
        {
            steps{
                sh 'echo "this is stage 4"'

            }
        }
    }
}
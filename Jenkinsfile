pipeline {
    agent any

   environment{
        Branch = 'Main'
        APP = 'Frontend'
   }

    stages {
        stage('STAGE1') {
            steps {
                sh '''
                    ls -lrt
                    sleep 5
                '''
                sh 'echo $Branch'
                echo "${env.Branch}"
                echo "${env.APP}"
                
            }
        }

        stage('STAGE2') {
            environment{
                name = 'tejas'
                age = '25'
            }
            steps {
                sh '''
                    pwd 
                    sleep 10
                    ls -lrt
                '''
                echo "${env.name}"
            }
        }

        stage('STAGE3') {
            steps {
                echo "This is Stage3"
                sh 'sleep 5'
            }
        }

        stage('STAGE4') {
            steps {
                 sh 'echo THis is STAGE4'
                 sh 'sleep 5'
            }
        }
    }
}
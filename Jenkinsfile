pipeline {
    agent any

    stages {
        stage('STAGE1') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sh '''
                    ls -lrt
                    sleep 5
                '''
                } 
            }
        }

        stage('STAGE2') {
            steps {
                try{
                    sh '''
                        exit 1
                        '''
                } catch (Exception e){
                    echo "caught an exception = ${e.message}"
                } finally{
                    echo "cleaning up"
                }
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
                sh 'echo This is STAGE4'
                sh 'sleep 5'
            }
        }
    }
}

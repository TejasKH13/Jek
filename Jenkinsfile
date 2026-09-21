pipeline {
    agent any

    stages {
        stage('STAGE1') {
            steps {
               sh '''
                    sleep 5
               '''
            }
        }

        stage('STAGE2') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    sh '''
                        exit 1
                    '''
                }

           
            }
        }

        stage('STAGE3') {
            steps {
                script {
                    try {
                        sh '''
                                exit 1
                        '''
                    } catch(Exception e) {
                        echo "Caught an Exception: ${e.message}"
                        
                    } finally {
                        echo "Cleaning up ....."
                    }
                }
            }
        }
        stage('STAGE4') {
            steps {
               sh '''
                    sleep 5
               '''
            }
        }
    }
}
pipeline {
    agent any

    stages {
        stage('stage1') {
            steps {
                script {
                    try {
                        echo "Running stage 1"

                        sh '''
                            sleep 10
                            ls -lt
                        '''

                        env.STAGE_1_STATUS = 'SUCCESS'
                    } catch (Exception e) {
                        echo "Caught the error and handling: ${e.message}"
                        env.STAGE_1_STATUS = 'FAILED'
                    }
                }
            }
        }

        stage('stage2') {
            when {
                expression {
                    env.STAGE_1_STATUS == 'SUCCESS'
                }
            }
            steps {
                echo "Executing stage 2"
                sh 'whoami'
            }
        }

        stage('stage3') {
            when {
                expression {
                    env.STAGE_1_STATUS == 'FAILED'
                }
            }
            steps {
                echo "Executing stage 3"
                sh 'uptime'
            }
        }

        stage('stage4') {
            steps {
                echo "Executing stage 4"
            }
        }
    }
}

// def stage1Status = ''

// def stage2Status = ''



// pipeline{

//     agent any

//     stages{

//         stage('Stage1'){

//             steps{

//                 script{

//                     try{

//                         sh '''

//                          sleep 10

//                          ls -lt

//                          '''

//                         stage1Status = 'SUCCESS'

//                     } catch(Exception e){

//                         echo "Caught the exception: ${e.message}"

//                         stage1Status = 'FAILED'

//                     }

//                 }

//             }

//         }

//         stage('Stage2'){

//             when{

//                 expression{

//                     stage1Status = 'SUCCESS'

//                 }

//             }

//             steps{

//                 echo "Running stage 2"

//                 sh '''

//                 pwd

//                 ls -lrt

//                 '''

//             }



//         }

//         stage('Stage3'){

//             when{

//                 expression{

//                     stage2Status == 'FAILED'

//                 }

//             }

//             steps{

//             echo "Running stage 3"

//             ls '''

//             date

//             ls -lrt

//             '''

//         }

        

//         }

//         stage('Stage4'){

//             steps{

//                 echo "Running stage 4"

//                 sh '''

//                 whoami

//                 find * -maxdepth 1 -type f

//                 '''

//             }



//         }

//     }

// }


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

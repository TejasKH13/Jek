pipeline{
    agent any
    parameters{
        string (defaultValue: 'main', description: 'Giving the branch to build and deploy', name: 'Branch')
        choice (choices: ['BUILD', 'COMPILE', 'TEST', 'DEPLOY'], 
        description: 'Giving option', 
        name: 'Env_choice')
        booleanParam defaultValue: true, description: 'uncheck this to deploy', name: 'Dry-run'
}
}

    
    stages{
        stage('stage1'){
            step{
                sh 'sleep 10'
                echo "Running stage 1"
            }
        stage('stage2'){
            step{
                sh 'sleep 10'
                sh '''
                    ls -lrt
                    pwd
                    date
                    '''
            }
        stage('stage3'){
            step{
                sh 'sleep 5'
                sh 'Echo running stage 3'
                sh 'uptime'
            }
        stage('stage4'){
            step{
                sh 'sleep 10'
                sh 'echo running stage 4'
            }
        }
        }
        }
        }
    }

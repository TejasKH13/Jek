pipeline {
    agent any

    parameters {
        string(
            defaultValue: 'main',
            description: 'Provide the branch to build and deploy',
            name: 'BRANCH'
        )

        choice(
            choices: ['TEST', 'QA', 'PRE-PROD', 'PROD'],
            description: 'Choose env to deploy',
            name: 'ENVIRONMENT'
        )

        booleanParam(
            defaultValue: true,
            description: 'Uncheck this to actually deploy',
            name: 'DRY-RUN'
        )
    }

    stages {
        stage('STAGE1') {
            steps {
                sh '''
                    ls -lrt
                    sleep 5
                '''

                echo "Branch = ${params.BRANCH}"
                echo "Name = ${params.ENVIRONMENT}"
                echo "Dry_run = ${params['DRY-RUN']}"
            }
        }

        stage('STAGE2') {
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
                sh 'echo This is STAGE4'
                sh 'sleep 5'
            }
        }
    }
}

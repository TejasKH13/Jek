pipeline {
    agent any
    stages {
        stage('STAGE1') {
            when {
                expression {
                    env.GIT_BRANCH == 'origin/main'
                }
            }
            steps {
                echo "Printing stage details"
                echo "${env.BUILD_NUMBER}"
                echo "${env.BUILD_NAME}"
                echo "${env.GIT_BRANCH}"
                echo "${env.GIT_URL}"
            }
            

        }
    }
}
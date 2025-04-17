pipeline {
    agent {
        label 'Agent-1'
    }    
    options{
        timeout(time: 10, unit: 'MINUTES')
        disableConcurrentBuilds()
    }
    environment {
        DEBUG = 'true'

    }
    stages{
        stage ('first stage'){
            steps{
                sh 'echo this is build'
            }
        }
    }
    post {
        always {
            echo 'this for every buil'
        }
        success {
            echo 'every success'
        }
        failure {
            echo 'if failure of build'
        }
    }
}

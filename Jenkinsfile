pipeline {
    agent { label 'AGENT-1' }
    environment {
        PROJECT = 'Expense'
        COMPONENT = 'Backend'
        DEPLOY_TO = 'production'
    }
    Stages {
        stage('test'){
            steps {
                script {
                    echo "Hello, this is a jenkins pipeline for $PROJECT - $COMPONENT"
                }
            }
        }
        stage('Build') {
            steps {
                script { 
                    withAWS(region: 'us-east-1', credentials: 'aws-creds')
                    echo "Building the project for $PROJECT - $COMPONENT"
                }
            }
        }
        stage('Deploy') {
            steps {
                withAWS(region: 'us-east-1', credentials: 'aws-creds') {
                sh """
                echo `deploying the project for $PROJECT - $COMPONENT to $DEPLOY_TO environment`
                """
            }
        }
    }
 }
    post {
        always {
            echo "always run this stage"
        }
        success {
            echo "this stage runs only on success"
        }
        failure {
            echo "this stage runs only on failure"    
        }
        unstable {
            echo "this stage runs only on unstable builds"
        }
}

}
pipeline {
    agent { label 'AGENT-1' }
    environment {
        PROJECT = 'Expense'
        COMPONENT = 'Backend'
        DEPLOY_TO = 'production'
    }
    stages{
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
                    
                    echo "Building the project for $PROJECT - $COMPONENT"
                }
            }
        }
        stage('Deploy') {
            steps {
                
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
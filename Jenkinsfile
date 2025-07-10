pipeline {
    agent { label 'AGENT-1' }
    environment {
        PROJECT = 'Expense'
        COMPONENT = 'Backend'
        DEPLOY_TO = 'production'
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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
                echo "This is a test deployment script"
                echo "You can replace this with actual deployment commands"
                echo "For example, you might run a script or use a deployment tool"
        
                echo "The person to greet is: ${params.PERSON}" 
                echo "The biography is: ${params.BIOGRAPHY}"
                echo "The toggle value is: ${params.TOGGLE}"    
                echo "The selected choice is: ${ps.CHOICE}"
                echo "The password is: ${params.PASSWORD}"

                """
            }
        }
        stage('Post Actions') {
            when {
                expression { params.PERSON == 'prakash' }
            }
            steps {
                script {
                    echo "This stage runs after the main stages"
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
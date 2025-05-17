/* pipeline {
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

     parameters {

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    }

    stages{
        stage ('first stage'){
            steps{
                sh 'echo this is build'
            }
        }

        stage ('second-params') {
            steps{
                
            }
        }
        stage('Approval'){
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
    }
    post {
        always {
            echo 'this for every buil'
            deleteDir()
        }
        success {
            echo 'every success'
        }
        failure {
            echo 'if failure of build'
        }
    }
}
 */

 pipeline{

    agent {

        label 'Agent-1'
    }
    parameters{
        choice(name: 'ACTION', choices: ['apply', 'destroy'], description: 'Pick something')
    }

    stages{
        stage('first'){
            steps{
                script{
                    sh """ 
                        echo "hi prakash"

                    """
                }
            }
        }
        stage('second'){
             when { 
                expression { params.ACTION == 'apply'}
            }
            steps{
                script{
                    sh """ 
                        echo "hi prakash"
                        echo "hello chinnari"

                    """
                }
            }
        }
        stage('three'){
            steps{
                script{
                    withAWS(region: 'us-east-1' , credentials: 'aws-cred')
                    sh """ 
                        echo "hi prakash"
                        echo "hello chinnari"

                    """
                }
            }
        }
    }
    post {
        always {
            echo "every time execute"
            deleteDir()
        }
        success{
            echo "only on sucess"
        }
        failure{
            echo "only on sucess"
        }

    }
 }
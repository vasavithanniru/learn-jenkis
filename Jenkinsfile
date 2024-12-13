pipeline {
    agent {
        label 'AGENT-1'
    } 
    stages {
        stage('Build') { 
            steps {
                sh 'echo this is build'
            }
        }
        stage('Test') { 
            steps {
                sh 'echo this is test' 
            }
        }
        stage('Deploy') { 
            steps {
                sh 'echo this is deploy'
            }
        }
        stage('Approval') {
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
    post{
        always{
            echo "This section runs always"
            deleteDir()
        }
        success{
            echo "This section runs when pipeline success"
        }
        failure{
            echo "This section runs when pipeline failure"
        }
    }
}
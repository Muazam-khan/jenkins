// Reference : https://www.jenkins.io/doc/book/pipeline/syntax
pipeline {  // pipeline is also a keyword, it means its a declarative approach
    agent any // is a directive or keyword
    environment{
        ENV_URL = "pipeline.google.com" //pipeline based var, also called global var, all tasks can access it
    }
    stages{  // is als a directive or keyword
        stage('Name of the stage - 1'){
            steps {
                sh 'echo how are you doing?'
                sh "echo Name of the variable is ${ENV_URL}"
            }
        }
        stage('Name of the stage - 2'){
            environment {
                ENV_URL = "task.google.com" // task or stage level var. nd this will hv higher priority than global
            }
            steps {
                sh "echo step1"
                sh "echo step2"
                sh "echo step3"

            }
        }
        stage('Name of the stage - 3'){
            steps {
                sh "echo step1"
                sh "echo step2"
                sh "echo step3"

            }
        }   
    }
}
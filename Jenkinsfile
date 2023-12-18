// Reference : https://www.jenkins.io/doc/book/pipeline/syntax
 pipeline {  // pipeline is also a keyword, it means its a declarative approach
       // agent any // is a directive or keyword, agent any means run on any of the available nodes
        agent any //{  // we want agent ws to run this task
            //label 'ws'
       // }
         environment {
            ENV_URL = "pipeline.google.com" //pipeline based var, also called global var, all tasks can access it
            SSH_CRED = credentials('SSH_CRED')
     }
      parameters {
            string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
            text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')        
       }
      options { 
                buildDiscarder(logRotator(numToKeepStr: '10'))
                timeout(time: 59, unit: 'MINUTES')
             }  //discard older than 10 logs
       triggers { 
                pollSCM('*/1 * * * *') // check ievery min if change in code and build
           }
     tools {
             maven 'maven-390' // to install maven software with help of tools on jenkins
       }
    stages{  // is als0 a directive or keyword
            stage('Name of the stage - 1'){
            steps {
                sh "hostname"
                sh "mvn --version"
                sh 'echo how are you doing Mr?'
                sh "echo Name of the variable is ${ENV_URL}"
                sh "env"
           }
        }
        stage('Demo on Parallel Stages'){
            parallel {
                stage('Download-1') {
                    steps {
                        sh "echo Download in Progress"
                        sh "sleep 30"
                    }
                }
                stage('Download-2') {
                    steps {
                        sh "echo Download in Progress"
                        sh "sleep 30"
                    }
                }
                stage('Download-3') {
                    steps {
                        sh "echo Download in Progress"
                        sh "sleep 30"
                    }
                }
            }

        }
          stage('Name of the stage- 2'){
            environment {
                ENV_URL = "stage.google.com" // task or stage level var. nd this will hv higher precedence than global or pipeline var
            }
            steps {
                sh "echo Name of the variable is ${ENV_URL}"
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
pipeline {
    agent any 
    stages {
        stage('Compile and Clean') { 
            steps {

                sh "clean compile"
            }
        }
        stage('Test') { 
            steps {
                sh "test site"
            }
            
             post {
                always {
                    junit allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml'   
                }
            }     
        }

        stage('deploy') { 
            steps {
                sh "package"
            }
        }
        
        stage('Archving') { 
            steps {
                 archiveArtifacts '**/target/*.jar'
            }
        }
    }
}

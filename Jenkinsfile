pipeline {

    agent any
       tools{
        maven "Maven 3.6.3"
        jdk "JDK-11"
    }  
        stages {
         stage('Build') {
             steps {
                 echo 'Building...'
             }
           stage('compile') {
      steps {
             echo "Compiling"
                bat 'mvn compile'
      }
             post {
                 always {
                     jiraSendBuildInfo site:'vaidehijirasite.atlassian.net', branch:'master'
                    
                 }
             }
         
           }
        }

    }   
}

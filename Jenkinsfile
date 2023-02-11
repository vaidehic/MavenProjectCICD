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
             post {
                 always {
                     jiraSendBuildInfo site:'vaidehijirasite.atlassian.net', branch:'master'
                    
                 }
             }
         

        }

    }   
}

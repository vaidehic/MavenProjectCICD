pipeline{
   agent any
    tools{
        maven "Maven 3.6.3"
        jdk "JDK-11"
    }  
  stages {
    stage ('build') {
      steps {
        echo "Building Project"
      }
    
   
     post {
        always {
           jiraSendBuildInfo site:'vaidehijirasite.atlassian.net', branch:'master'
        }
     }
  }
  }


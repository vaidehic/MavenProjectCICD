pipeline{
   agent any
    tools{
        maven "Maven 3.6.3"
        jdk "JDK-11"
    }  
   stages{
    stage('compile') {
      steps {
        echo "Compiling"
        bat 'mvn compile'
      }
    }
    stage('test') {
      steps {
        echo "test"
        bat 'mvn test'
      }
    }
      stage ('build') {
         steps {
            echo "building"
         }
      
     post {
        always {
           jiraSendBuildInfo site: 'vaidehijirasite.atlassian.net', branch:'MPC-1-develop'
        }
     }
  }
}
}

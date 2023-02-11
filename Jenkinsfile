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
    }
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
    stage('Sonar Analaysis') {
      steps {
        echo "Performing Sonar Analysis"
        withSonarQubeEnv('SonarQubeServer'){
        bat 'mvn sonar:sonar'
        }
      }
    }
     post {
        always {
           jiraSendBuildInfo site:'vaidehijirasite.atlassian.net', branch:'master'
        }
     }
  }
}

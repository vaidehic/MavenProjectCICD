pipeline {

    agent any
       tools{
        maven "Maven 3.6.3"
        jdk "JDK-11"
    }  
        stages {
            stage('test') {
      steps {
        echo "test"
        bat 'mvn test'
      }
    }
            stage('Publishing Junit report') {
                steps {
                    junit 'target/surefire-reports/**/*.xml'
                }
            }
  

    }   
}

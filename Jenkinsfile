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
            stage('Publishing Junit report') {
                steps {
                    junit 'target/surefire-reports/**/*.xml'
                }
            }
  
           
            
            stage('Upload Artifact') {
                 steps {
                  script{
                      def server = Artifactory.server 'artifactory'
                      def uploadSpec = """{ 
                          "files":[
                              {
                                  "pattern":"target./*.jar",
                                  "target": "multibranchCiCdvaidehi/"
                              }
                              ]
                              }"""
                              server.upload(uploadSpec)
                              }
                              }
                              }
            }             

    }   


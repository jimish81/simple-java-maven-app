pipeline {
 agent any
 tools {
  maven 'maven3.6.0'
  jdk 'java1.8.0'
 }
 stages {
  stage('Build') {
   steps {
    sh "mvn -B -DskipTests clean package"
   }
  }
  stage('Test') {
   steps {
    sh 'mvn test'
   }
   post {
    always {
     junit 'target/surefire-reports/*.xml'
    }
   }
  }

  stage('Publish') {
   steps {
    //sh 'curl -X PUT -u jimish:APARmshG1mhGExY41HfTjXX5Z8x -T target/my-app-1.0-SNAPSHOT.jar "http://54.71.49.80:8081/artifactory/libs-release/my-app-1.0-SNAPSHOT.jar"'
      sh 'curl -X PUT -u jimish:AP3uwHcum9qbRD5rQM8UH8r2NCj -T target/my-app-1.0-SNAPSHOT.jar "http://35.200.196.173:8081/artifactory/test/my-app-1.0-SNAPSHOT.jar"'   
   }
  }

 }
}

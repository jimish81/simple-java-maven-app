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
  stage('Deploy') {
   steps {
    sh 'java -jar target/my-app-1.0-SNAPSHOT.jar'
   }
  }
  stage('Publish') {
   steps {
    sh 'curl -X PUT -u jimish:28326323 -T Maven-Upload-1.1.jar "http://54.71.49.80:8081/artifactory/libs-release/my-app-1.0-SNAPSHOT.jar"'
   }
  }

 }
}

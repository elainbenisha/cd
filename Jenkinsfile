pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 bat "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: '9b9b593d-5e02-4e94-8c7c-94ee7993356d', path: '', url: 'http://localhost:8080/')], contextPath: '/cd', war: '**/*.war'
 }
 }
 }
 }
}

node
{
  def mavenhome= tool name: 'maven'
  stage('checkout')
  {
    git branch: 'dev', changelog: false, poll: false, url: 'https://github.com/sathishyadava143/maven-web-application.git'
  }
  stage('build')
  {
  sh "${mavenhome}/bin/mvn clean package"
  }
  /*stage('sonarreport')
  {
  sh "${mavenhome}/bin/mvn sonar:sonar"
  }
  stage('upload_to_artifact_repo')
  {
  sh "${mavenhome}/bin/mvn clean deploy"
  }
 stage('deploy app')
  {
  sshagent(['9b306c62-85d3-4c5f-bd6b-00c9d77bdc07']) {
    sh "scp -o StrictHostKeyChecking=no target/*.war ubuntu@3.109.56.226:/opt/tomcat/webapps/"
}
  }
  stage('build notification'){
      emailext body: 'hello build success', subject: 'test jenkins', to: 'sathishyadav532@gmail.com'
  }/*
}

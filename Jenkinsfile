node
{
  def mavenhome= tool name: 'maven3.9.9'
  stage('checkout')
  {
  git credentialsId: '8c8c5e46-ae4d-4f81-ad28-6c200d3fbefb', url: 'https://github.com/sathishyadava143/maven-web-application.git'
  }
  stage('build')
  {
  sh "${mavenhome}/bin/mvn clean package"
  }
  stage('sonarreport')
  {
  sh "${mavenhome}/bin/mvn sonar:sonar"
  }
  stage('upload_to_artifact_repo')
  {
  sh "${mavenhome}/bin/mvn clean deploy"
  }
 stage('deploy app')
  {
  sshagent(['4737f250-498f-45fd-821a-5731cc39999c']) {
    sh "scp -o StrictHostKeyChecking=no target/*.war ec2-user@13.127.202.254:/opt/apache-tomcat-9.0.94/webapps/"
}
  }
  stage('build notification'){
      emailext body: 'hello build success', subject: 'test jenkins', to: 'sathishyadav532@gmail.com'
  }
}

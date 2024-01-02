Pipeline{
  agent { label 'Slave1' }
  tools{
    jdk 'Java17'
    maven 'Maven3'
  }
  Stages{
    stage("Cleanup Workspace"){
         steps{
         cleanWs()
         }
  }
    stage("checkout from SCM"){
      steps{
        git branch: 'main', credentialsId: 'github', url: 'https://github.com/HarshalAvaghanji/register-app.git'
      }
}
    stage("Build Application"){
      steps{
        sh "mvn clean package"
      }
}
    stage("Test application"){
      steps{
        sh "mvn test"
      }
    }
  }
}

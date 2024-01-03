pipeline{
  agent { label 'Slave1' }
  tools{
    jdk 'Java17'
    maven 'Maven3'
  }
  stages{
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
    stage("SonaQube Analysis"){
      steps{
        script{
          withSonarQubeEnv(credentialsId: 'token'){
                       sh "mvn sonar: sonar"
          }
        }
      }
    }
  }
}

pipeline{
    agent any
     tools{
      maven "Maven.3.8.6"
      }
    stages{
     stage('Build Maven'){
       steps{
          checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/chavez46711/devops-automation']]])
          echo 'mvn clean install .'
        }
      }

       stage('Build Docker Image'){
         steps{
          script{
              echo 'docker buil -t administrador/devops-integration .'
        }
      }
    }

      stage('Push image to hub'){
         steps{
          script{
      withCredentials([string(credentialsId: 'DockerJenkins', variable: 'docker')]) {
       echo 'docker login -u administrador -p $ {docker}'
}
               echo 'docker push administrador/devops-integration'
        }
      }
    }

   }
}


pipeline {
   environment {
    registry = "aryangupta4460/myweb"
    registryCredential = 'dockerHub'
    dockerImage = ''
  }

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/Aryan-Gupta4460/JenkinExe.git'
      }
    }

    stage('Build image') {
      steps{
        script {
         dockerImage = docker.build registry + ":$BUILD_NUMBER"          
        }
      }
    }

    stage('Push Image') {
      steps{
        script {
           docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }

    stage('Deploy App to local k8s') {
      steps {
        script {
          sh 'kubectl apply -f myweb.yaml'
        }
      }
    }

  }

}

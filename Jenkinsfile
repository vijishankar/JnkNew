pipeline {
   environment {
    registry = "aryangupta4460/myweb"
    registryCredential = 'dockerHub'
    dockerImage = ''
  }

  agent any

  stages {

    stage('Deploy App to local k8s') {
      steps {
        script { 
           sh 'kubectl apply -f Deployment.yaml'
           sh 'kubectl apply -f Service.yaml'
               
        }
      }
    }

  }

}

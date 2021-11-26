pipeline {
  agent any
    stage('Apply Kubernetes Files') {
      steps {
          withKubeConfig([credentialsId: '3565b99f-b63f-4e3c-85d2-8f55a7c2f1c9']) {
          sh 'cat deployment.yaml | sed "s/{{BUILD_NUMBER}}/$BUILD_NUMBER/g" | kubectl apply -f -'
          sh 'kubectl apply -f service.yaml'
        }
      }
  }
}
post {
    success {
      slackSend(message: "Pipeline is successfully completed.")
    }
    failure {
      slackSend(message: "Pipeline failed. Please check the logs.")
    }
}
}

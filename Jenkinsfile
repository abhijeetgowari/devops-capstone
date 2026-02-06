pipeline {
  agent any

  stages {
    stage('Clone') {
      steps {
        echo "code done"
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t capstone-backend ./backend'
      }
    }

    stage('Deploy to K8s') {
      steps {
        sh '''
          kubectl apply -f k8s/deployment.yaml
          kubectl apply -f k8s/service.yaml
        '''
      }
    }
  }
}

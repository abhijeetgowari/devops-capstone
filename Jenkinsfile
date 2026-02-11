pipeline {
  agent any

  stages {
    stage('Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/abhijeetgowari/devops-capstone.git'       
        echo "code done"
      }
    }

    stage('Build Docker Image') {
      steps {
      sh 'docker build -t capstone-backend .'      
      echo "Build Docker Done"
      }
    }

    stage('Deploy to K8s') {
      steps {
        sh ' ' '
        kubectl apply -f deployment.yaml
        kubectl get deployments
        kubectl get pods -o wide
        
        ' ' ' 
         echo "Deploy done"
      }
    }
  }
}

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
      sh 'docker build -t node-app-image:v1 .' 
      sh 'docker run -d -p 5053:5050 node-app-image:v1'    
        echo "Build Docker Done"
      }
    }

    stage('Deploy to K8s') {
      steps {
        withKubeConfig([ 'minikube-config':'my-kubeconfig-id']){
        sh 'kubectl get nodes'
        sh 'kubectl apply -f deployment.yaml'
        sh 'kubectl get deployments'
        sh 'kubectl get pods -o wide'
         echo "Deploy done"
        sh 'kubectl apply -f service.yaml'
        sh 'kubectl get svc'
        }
      }
    }
  }
}

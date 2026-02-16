pipeline {
 agent any

 environment {
  DOCKERHUB_CREDS = credentials('prathameshwaingade')
 }

 stages {

  stage('Clone Repo') {
   steps {
    git 'https://github.com/Microservices-Project-main/microservices-project.git'
   }
  }

  stage('Build') {
   steps {
    sh 'mvn -f service-user/pom.xml clean package'
    sh 'npm install --prefix service-order'
   }
  }

  stage('Build Docker Images') {
   steps {
    sh 'docker build -t user-service ./service-user'
    sh 'docker build -t order-service ./service-order'
   }
  }

  stage('Push Images') {
   steps {
    sh 'docker login -u $DOCKERHUB_CREDS_USR -p $DOCKERHUB_CREDS_PSW'
    sh 'docker tag user-service prathameshwaingade/user-service:latest'
    sh 'docker push prathameshwaingade/user-service:latest'
   }
  }

  stage('Deploy to Kubernetes') {
   steps {
    sh 'kubectl apply -f k8s/'
   }
  }

 }
}

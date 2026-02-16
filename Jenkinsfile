pipeline {
 agent any

 environment {
  DOCKERHUB_CREDS = credentials('sakshipardeshi')
 }

 stages {

  stage('Clone Repo') {
   steps {
    git 'https://github.com/yourrepo/microservices-project.git'
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
    sh 'docker tag user-service yourdockerhub/user-service:latest'
    sh 'docker push yourdockerhub/user-service:latest'
   }
  }

  stage('Deploy to Kubernetes') {
   steps {
    sh 'kubectl apply -f k8s/'
   }
  }

 }
}

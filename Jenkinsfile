pipeline {
  agent any

  environment {
    IMAGE      = "123456789009873/flask-app"
    TAG        = "${BUILD_NUMBER}"
    APP_SERVER = "13.233.131.39"
  }

  stages {
    stage('Checkout') {
      steps { checkout scm }
    }

    stage('Build Image') {
      steps { sh "docker build -t ${IMAGE}:${TAG} -t ${IMAGE}:latest ./app" }
    }

    stage('Push to Docker Hub') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-creds',
                          usernameVariable: 'DH_USER', passwordVariable: 'DH_PASS')]) {
          sh 'echo "$DH_PASS" | docker login -u "$DH_USER" --password-stdin'
          sh "docker push ${IMAGE}:${TAG}"
          sh "docker push ${IMAGE}:latest"
        }
      }
    }

    stage('Deploy to App Server') {
      steps {
        withCredentials([sshUserPrivateKey(credentialsId: 'app-server',
                          keyFileVariable: 'KEY', usernameVariable: 'SSH_USER')]) {
          sh """
            ssh -o StrictHostKeyChecking=no -i \$KEY \$SSH_USER@${APP_SERVER} '
              docker pull ${IMAGE}:${TAG};
              docker rm -f flask-app || true;
              docker run -d --name flask-app --restart always -p 5000:5000 ${IMAGE}:${TAG}
            '
          """
        }
      }
    }

    stage('Health Check') {
      steps {
        sh "sleep 5 && curl -f http://${APP_SERVER}:5000"
      }
    }
  }

  post {
    always { sh 'docker logout || true' }
  }
}

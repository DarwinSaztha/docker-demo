pipeline {
  agent any

  stages {
    stage('Clone Repo') {
      steps {
        git branch: 'main', url: 'https://github.com/<your-username>/docker-jenkins-demo.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t demo-webapp .'
      }
    }

    stage('Run Container') {
      steps {
        sh '''
        docker rm -f demo-web-container || true
        docker run -d -p 8081:80 --name demo-web-container demo-webapp
        '''
      }
    }
  }
}

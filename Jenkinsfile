pipeline {
  agent any
  stages {
    stage('Clone Repository') {
      steps {
        git(url: 'https://github.com/your-username/your-repo.git', credentialsId: "${GITHUB_CREDENTIALS}")
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Run Tests') {
      steps {
        sh 'npm test'
      }
    }

    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }

    stage('Deploy') {
      when {
        branch 'main'
      }
      steps {
        echo 'Deploying to production...'
      }
    }

  }
  environment {
    GITHUB_CREDENTIALS = credentials('github-credentials-id')
  }
  post {
    always {
      echo 'Build process complete.'
    }

    success {
      echo 'Build succeeded!'
    }

    failure {
      echo 'Build failed!'
    }

  }
}
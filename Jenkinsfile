pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/lucrada/JenkinsTest.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Lint') {
      steps {
        sh 'npm run lint'
      }
    }

    stage('Flow') {
      steps {
        sh 'npm run flow'
      }
    }

    stage('Test') {
      steps {
        sh 'npm run test'
      }
    }
  }

  post {
    always {
      junit '**/coverage/clover.xml'
      publishCoverage adapters: [cobertura(coberturaReportFile: 'coverage/cobertura-coverage.xml')]
    }
  }
}
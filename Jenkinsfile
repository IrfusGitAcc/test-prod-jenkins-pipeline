pipeline {
  agent none
  stages {
    stage('Deploy to Test') {
      agent { label 'test-agent' }
      steps {
        checkout scm
        sh 'cp index.html /var/www/app/index.html'
        sh 'ls -l /var/www/app'
      }
    }
    stage('Approve Prod') {
      steps { input message: 'Deploy to PROD?' }
    }
    stage('Deploy to Prod') {
      agent { label 'prod-agent' }
      steps {
        checkout scm
        sh 'cp index.html /var/www/app/index.html'
        sh 'ls -l /var/www/app'
      }
    }
  }
}

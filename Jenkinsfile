pipeline {
  agent { docker { image 'python:3.7.2' } }
  stages {
    stage('build') {
      steps {
        sh 'pip install -r requirements.txt'
      }
    }
    stage('test') {
      steps {
        sh 'py.test test.py  --junitxml=reports/reports.xml'
      }
      post {
        always {
          junit 'reports/*.xml'
        }
      }
    }
  }
}
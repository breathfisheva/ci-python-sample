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
        sh ' pytest test.py --html=reports/reports.html'
      }
      post {
        always{
            script{
                node(win_node){
                    publishHTML (target: [
                        allowMissing: false,
                        alwaysLinkToLastBuild: false,
                        keepAll: true,
                        reportDir: 'reports',
                        reportFiles: 'reports.html',
                        reportName: "HTML Report"
                    ])
                }
            }
        }
      }
    }
  }
}
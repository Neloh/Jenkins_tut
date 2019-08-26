pipeline {
  agent { docker { image 'python:3.7.2' } }
  stages {
    stage('build') {
      steps {
        sh """
        . venv/bin/activate
        pip install -r requirements.txt
        """
      }
    }
    stage('test') {
      steps {
        sh """
        . venv/bin/activate
        python test.py
        """
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }    
    }
  }
}

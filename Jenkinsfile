pipeline {
  agent { docker { image 'python:3.6.5' } }
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

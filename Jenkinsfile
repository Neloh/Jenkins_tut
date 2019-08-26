pipeline {
  agent { docker { image 'python:3.7.2' } }
  stages {
    stage('build') {
      steps {
        sh """
        echo $PYTHON_INTERPRETER
        . ~/venv/bin/activate
        pip install -r requirements.txt
        """
      }
    }
    stage('test') {
      steps {
        sh """
        $PYTHON_INTERPRETER test.py
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

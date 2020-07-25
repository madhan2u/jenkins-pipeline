pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Build the Application'
          }
        }

        stage('Test') {
          steps {
            echo 'Testing the Application'
            echo "Bearer token is ${PaaSToken}"
          }
        }

        stage('Test Log') {
          steps {
            writeFile(file: 'TestLogFile.txt', text: 'This is a test log file')
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        input(message: 'Do you want to deploy?', id: 'OK')
        echo 'Deploying the Application'
      }
    }

  }
  environment {
    PaaSToken = 'kafld3242345jl;23k5hl542lk52'
  }
}
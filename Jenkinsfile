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
          environment {
            LocalVariable = 'Local test data new variable'
          }
          steps {
            writeFile(file: 'TestLogFile.txt', text: "This is a log file, Global Variable ${PaaSToken} and Local data: ${LocalVariable}")
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        when {
          branch "master"
        }
        stage('Deploy') {
          steps {
            input(message: 'Do you want to deploy?', id: 'OK')
            echo 'Deploying the Application'
          }
        }

        stage('Archive Files') {
          steps {
            archiveArtifacts 'TestLogFile.txt'
          }
        }

      }
    }

  }
  environment {
    PaaSToken = 'kafld3242345jl;23k5hl542lk52'
  }
}
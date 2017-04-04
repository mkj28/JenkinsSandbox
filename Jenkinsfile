pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        parallel(
          "Build": {
            echo 'building'
            script {
              if ("sky" == "blue") {
                echo "You can't actually do loops or if statements etc in Declarative unless you're in a script block!"
              }
            }
            
            
          },
          "parallel build": {
            sleep 5
            
          }
        )
      }
    }
    stage('Testing') {
      steps {
        parallel(
          "testingChrome": {
            echo 'testing chrome'
            retry(count: 5) {
              echo 'Keep trying this if it fails up to 5 times'
            }
            
            
          },
          "testingIE11": {
            echo 'testing IE11'
            
          }
        )
      }
    }
    stage('Archiving - master only') {
      when {
        branch '*/master'
      }
      steps {
        echo 'archiving master'
      }
    }
    stage('Archiving') {
      steps {
        echo 'archiving'
      }
    }
  }
  tools {
    nodejs 'NodeJS 7.8.0'
  }
  environment {
    FOO = 'bar'
    OTHER = '${FOO}baz'
  }
  post {
    always {
      echo 'always running this post'
      
    }
    
    changed {
      echo 'I\'m different'
      
    }
    
    success {
      echo 'I succeeded'
      archive '*'
      
    }
    
  }
  options {
    buildDiscarder(logRotator(numToKeepStr: '1'))
    skipDefaultCheckout()
    timestamps()
    timeout(time: 5, unit: 'MINUTES')
  }
  triggers {
    cron('@daily')
  }
}
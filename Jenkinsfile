pipeline {
  agent any
  
  parameters {
    choice(choices: 'Retail\nTravel\nHotel\nFinancial\nCommunication\n', description: 'Specify Dataset', name: 'dataset')
    choice(choices: 'Eric Middleton: 4151234567\nMichael McCarron: 4151234566\n', description: 'Phone Number', name: 'phoneNumber')
  }

  stages {
    stage('Resetting demo') {
      steps {
        echo "demo: ${params.dataset}"
        echo "demo: ${params.phoneNumber}"
        echo 'building'
        script {
          if ("sky" == "blue") {
            echo "You can't actually do loops or if statements etc in Declarative unless you're in a script block!"
          }
        }
      }
    }
    stage('Testing') {
      steps {
        parallel(
          "testingChrome": {
            echo 'testing chrome'
            retry(5) {
              echo 'Keep trying this if it fails up to 5 times'
            }
          },
          "testingIE11": {
            echo 'testing IE11'
          },
          "testing another browser": {
            sleep 5
          }
        )
      }
    }
    stage('Archiving - master only') {
      when {
        branch "master"
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
    buildDiscarder(logRotator(numToKeepStr: '10'))
    timestamps()
    timeout(time: 5, unit: 'MINUTES')
  }
  triggers {
    pollSCM('* * * * *')
  }
}
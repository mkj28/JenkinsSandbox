pipeline {
  agent any

  stages {
    stage("Build") {
      steps {
        echo "building"
        script {
          if ("sky" == "blue") {
            echo "You can\'t actually do loops or if statements etc in Declarative unless you\'re in a script block!"
          }
        }
      }
    }
    stage("Testing") {
      steps {
        parallel(
          testingChrome: {
            echo "testing chrome"
            retry(5) {
              echo "Keep trying this if it fails up to 5 times"
              }
          },
          testingIE11: {
            echo "testing IE11"
          }
        )
      }
    }
    stage("Archiving") {
      when {
        branch ‘*/master’
      }
      steps {
        echo "archiving master"
        }
    }
  }
}
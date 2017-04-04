pipeline {
  agent any

  stages {
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
  }
}
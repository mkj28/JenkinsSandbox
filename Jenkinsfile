pipeline {
  agent any

  environment {
    FOO = "bar"
    OTHER = "${FOO}baz"
  }

  tools {
    nodejs "NodeJS 7.8.0"
  }

  options {
    // General Jenkins job properties
    buildDiscarder(logRotator(numToKeepStr:'1'))
    // Declarative-specific options
    skipDefaultCheckout()
    // "wrapper" steps that should wrap the entire build execution
    timestamps()
    timeout(time: 5, unit: 'MINUTES')
  }

  triggers {
    cron('@daily')
  }

  stages {
    stage("Build") {
      steps {
        echo "building"
        script {
          if ("sky" == "blue") {
            echo "You can't actually do loops or if statements etc in Declarative unless you're in a script block!"
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
    stage("Archiving - master only") {
      when {
        branch "*/master"
      }
      steps {
        echo "archiving master"
        }
    }
    stage("Archiving") {
      steps {
        echo "archiving"
        }
    }
  }
  post {
    always {
      echo "always running this post"
    }
    changed {
      echo "I'm different"
    }
    success {
      echo "I succeeded"
      archive "*"
    }
  }
}

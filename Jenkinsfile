pipeline {
  agent any
  
  parameters {
    booleanParam(defaultValue: true, description: 'Run stage1?', name: 'stage1')
    booleanParam(defaultValue: true, description: 'Run stage2?', name: 'stage2')
    booleanParam(defaultValue: true, description: 'Run stage3?', name: 'stage3')
  }

  stages {
    stage('Stage 1') {
      when {
        expression { params.stage1 }
      }
      steps {
        echo "Running stage 1"
      }
    }
    stage('Stage 2') {
      when {
        expression { params.stage2 }
      }
      steps {
        echo "Running stage 2"
      }
    }
    stage('Stage 3') {
      when {
        expression { params.stage3 }
      }
      steps {
        echo "Running stage 3"
      }
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
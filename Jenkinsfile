pipeline {
  agent any
    
  stages {
    stage('Run stage 1?') {
      steps {
        input message: 'Select if you want to run stage 1. Abort will abort everything.', parameters: [booleanParam(defaultValue: true, description: 'Run stage1?', name: 'stage1')]
      }
    }
    stage('Stage 1') {
      when {
        expression { params.stage1 }
      }
      steps {
        echo "Running stage 1"
      }
    }
    stage('Run stage 2?') {
      steps {
        input message: 'Select if you want to run stage 2. Abort will abort everything.', parameters: [booleanParam(defaultValue: true, description: 'Run stage2?', name: 'stage2')]
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
    stage('Run stage 3?') {
      steps {
        input message: 'Select if you want to run stage 3. Abort will abort everything.', parameters: [booleanParam(defaultValue: true, description: 'Run stage3?', name: 'stage3')]
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
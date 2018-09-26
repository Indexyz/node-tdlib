pipeline {
  agent {
    docker {
      image 'node'
    }
  }
  
  stages {
    stage('install deps') {
      steps {
        sh 'npm install -g cmake-js'
        sh 'apt-get update && apt-get install -y g++ ccache openssl libssl-dev cmake gperf make git libreadline-dev zlib1g-dev' 
      }
    }
    
    stage('build') {
      steps {
        sh 'cmake-js -D'
      }
    }
    
    stage('release') {
      steps {
        archiveArtifacts artifacts: 'build/Debug/tdlib.node', fingerprint: true
      }
    }
  }
}

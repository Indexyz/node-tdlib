pipeline {
  agent {
    docker {
      image 'node'
    }
  }
  
  stages {
    stage('install deps') {
      sh 'npm install -g cmake-js'
      sh 'apt-get update && apt-get install cmake gcc openssl-dev zlib-dev gperf'
    }
    
    stage('build') {
      sh 'cmake-js -D'
    }
    
    stage('release') {
      archiveArtifacts artifacts: 'build/Debug/tdlib.node', fingerprint: true
    }
  }
}

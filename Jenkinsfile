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
        sh 'echo "deb http://ftp.debian.org/debian jessie-backports main" >> /etc/apt/sources.list'
        sh 'apt-get update && apt-get -t jessie-backports install -y --no-install-recommends cmake'
        sh 'apt-get update && apt-get install -y g++ ccache openssl libssl-dev gperf clang make git libreadline-dev zlib1g-dev' 
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

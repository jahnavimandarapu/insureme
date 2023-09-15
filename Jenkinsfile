pipeline {
  agent any
  tools {
    maven 'M2_HOME'
        }
stages {
  stage('git checkout') {
  steps {
   git 'https://github.com/jahnavimandarapu/insureme.git'
  }
}
  stage('build package'){
    steps {
      sh 'mvn package'
    }
  }
  stage('publish html reports'){
    steps {
      publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '/var/lib/jenkins/workspace/InsureMe-Project/target/surefire-reports', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true]) 
    }
    }
  }
}
  
  

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
  stage('building docker image'){
    steps {
      sh 'docker build -t mandarapujahnavi/insureme-app:1.0 .'
    }
      
       }
  stage ('docker image push'){
    steps {
      withCredentials([string(credentialsId: 'dockerHubPwd', variable: 'hub2docker')]) {
      sh 'docker login -u mandarapujahnavi -p ${hub2docker}'
      }
      sh 'docker push mandarapujahnavi/insureme-app:1.0'   
    }
  }
        
  }
  }
}
  
  

pipeline {
  agent any
  stages {
    stage('message') {
      steps {
        echo 'hello world'
      }
    }
     stage('test'){
      steps{
        script{
          bat 'ng test --no-watch --no-progress --browsers=ChromeHeadless'
        }
      }
    }
    stage('build'){
      steps{
        script{
          bat 'npm install'
          bat 'ng build'
        }
      }
    }
   

  }
}
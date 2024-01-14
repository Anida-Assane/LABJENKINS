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
    stage('archive on nexus3'){
      steps{
        script{
        nexusArtifactUploader(
        nexusVersion: 'nexus3',
        protocol: 'http',
        nexusUrl: 'http://localhost:8081',
        groupId: 'com.example',
        version: 1,
        repository: 'JenkinksAngularLab',
        credentialsId: 'nexusCredential',
        artifacts: [
            [artifactId: labJenkins,
             classifier: '',
             file: 'dist'+ version +'.zip',
             type: 'zip']
        ]
     )
        }
      }
    }
   

  }
}
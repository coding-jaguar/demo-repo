pipeline {
  agent any

  stages {
    stage("build frontend"){
      steps{
        echo "building the application"
        nodejs(nodeJSInstallationName: 'node-22.5.1') {
          sh 'npm install'
          sh 'npm install -g serve'
          sh 'npm run build'
        }
      }
    }
    stages("run build"){
      steps{
        echo "running the application"
        nodejs() {
          sh 'serve -s build'
        }
      }

    }
  }
}
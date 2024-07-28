pipeline {
  agent any

  stages {
    stage("build frontend"){
      steps{
        echo "building the application"
        nodejs(nodeJSInstallationName: 'node-22.5.1') {
          sh 'npm install'
          sh 'npm run build'
        }
      }
    }
    stages("deploy"){
      steps {
                echo 'Deploying...'
                // Copy files to Windows localhost
                sshPublisher(publishers: [sshPublisherDesc(
                    configName: 'localhost-windows', 
                    transfers: [sshTransfer(
                        sourceFiles: 'build/**', 
                        remoteDirectory: 'D:\\deakinHomework\\tri2-2024\\ppit\\deployment',
                        removePrefix: 'build',
                        execCommand: 'D:\\deakinHomework\\tri2-2024\\ppit\\deployment\\your-deployment-script.bat'
                    )],
                    usePromotionTimestamp: false,
                    useWorkspaceInPromotion: false,
                    verbose: true
                )])
            }

    }
  }
}
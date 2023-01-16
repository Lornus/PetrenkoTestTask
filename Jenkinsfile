pipeline{
      agent {
        docker {
            image 'node:lts-bullseye-slim' 
            args '-p 3000:3000' 
        }
    }
stages{
  stage("Build"){
    steps{
        sh "echo 'Init'"
        script{
            sh "pwd && ls -la"
             sh "npm ci"
    }
    }
  }
    stage("Run tests"){
      steps{
        sh "echo 'run tests headless'"
      script{
            
            sh "npm run test"
      }
      }
    }
  }
  post{
    cleanup{
      script{
        sh label: 'Cleanup working directoty', script: """
        echo "Cleaning work directory..."
        rm -rf /var/jenkins_home/workspace/automation
        rm -rf .git*
        ls -a
        """
      }
    }
  }
    
}

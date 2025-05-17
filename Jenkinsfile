pipeline {
    agent any
    tools {
        nodejs 'node18'
  }
    environment {
        GIT_CREDENTIALS_ID = "d24121e7-c5e6-413f-a8c4-890f7eeee1fc"
        GIT_REPO = 'https://github.com/SaiRamya15/nodejspipeline.git'
        GIT_BRANCH = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: "${GIT_BRANCH}",
                    credentialsId: "${GIT_CREDENTIALS_ID}",
                    url: "${GIT_REPO}"
            }
        }

        stage('Build') {
            steps {
                bat 'npm install'
                bat 'node index.js'
            }
        }

       

   }
}

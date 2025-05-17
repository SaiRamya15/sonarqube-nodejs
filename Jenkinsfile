pipeline {
    agent any
    tools {
        nodejs 'node18'
  }
    environment {
        GIT_CREDENTIALS_ID = "d24121e7-c5e6-413f-a8c4-890f7eeee1fc"
        GIT_REPO = 'https://github.com/SaiRamya15/nodejspipeline.git'
        SONAR_SCANNER_HOME = tool 'sonarqube' // Matches the name in Jenkins
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
        
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarQube') {
                    sh "${SONAR_SCANNER_HOME}/bin/sonar-scanner"
                }
            }
        }
    }
}

       

   

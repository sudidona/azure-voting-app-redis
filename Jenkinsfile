@Library('github.com/devbyaccident/demo-shared-pipeline@test-branch') _

pipeline {
    agent any

    stages {
      stage('Verify branch'){
        steps{
          echo "$GIT_BRANCH"
        }
      }
      stage('Docker Build'){
        steps{
          sh 'docker images -a'
          sh("""
            cd azure-vote/
            docker images -a
            docker build -t jenkins-pipeline .
            docker images -a
            cd ..
          """)
        }
      }
    }
}

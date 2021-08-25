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
          pwsh(script: 'docker image -a')
          pwsh(script: """
            cd azure-vote/
            docker image -a
            docker build -t jenkins-pipeline .
            docker image -a
            cd ..
          """)
        }
      }
    }
}

pipeline {
  ...

  stages {
    stage('Compile') {
      steps {
        sh 'go build'
      }
    }

    stage('Test') {
      steps {
        sh 'go test ./...'
      }
    }

    stage ('Release') {
      when {
        buildingTag()
      }

      environment {
        GITHUB_TOKEN = credentials('github-token')
      }

      steps {
        sh 'curl -sfL https://goreleaser.com/static/run | bash'
      }
    }
  }
}

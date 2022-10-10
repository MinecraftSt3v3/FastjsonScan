pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        sh 'go build'
      }
    }

    stage ('Release') {
      environment {
        GITHUB_TOKEN = credentials('github-token')
      }

      steps {
	sh 'goreleaser release --rm-dist'
      }
    }
  }
}

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
	sh 'git config --global user.name "Ryan Hoofard"'
	sh 'git config --global user.email "rhoofard2000@gmail.com"'
	sh 'git tag -a v0.1.23 -m "First release"'
	sh 'goreleaser release --rm-dist'
      }
    }
  }
}

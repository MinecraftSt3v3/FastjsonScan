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
	sh 'git config --global user.name "Steven Mendez"'
	sh 'git config --global user.email "mendez.steven99@gmail.com"'
	sh 'git tag -a v0.1.23 -m "First release"'
	sh 'goreleaser release --rm-dist'
      }
    }
  }
}

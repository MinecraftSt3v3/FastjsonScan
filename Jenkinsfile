pipeline {
  ...

  stages {
    stage('Compile') {
      steps {
        sh 'goreleaser build --rm-dist'
      }
    }

    stage('Test') {
      steps {
        echo 'Passed the first stage'
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
      	sh 'goreleaser release --snapshot --rm-dist'
      }
    }
  }
}

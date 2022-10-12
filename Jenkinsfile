pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
      	sh 'goreleaser build --rm-dist'
      }
    }

    stage ('Release') {
      	when {
		expression {
		   env.BRANCH_NAME == 'main'
		}
	    }

      steps {
	      sh 'curl -u admin:password123 -X PUT "172.17.0.2:8081/artifactory/libs-release/junit-4.13.3-SNAPSHOT.jar" -T "/home/alpuser/.jenkins/workspace/jenkins-releaser/target/junit-4.13.3-SNAPSHOT.jar"'
	//sh 'goreleaser release --rm-dist'
      }
    }
  }
}

pipeline {
  agent {
	any {
	  args '-v /root/.m2:/root/.m2'
	}
  }
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
	sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'Testing..'
          }
        }
        stage('error') {
          steps {
            sleep 2
          }
        }
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }
  }
  environment {
    args = '-v /root/.m2:/root/.m2'
  }
}

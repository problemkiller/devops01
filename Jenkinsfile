pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
	sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'Testing..'
          }
	  post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
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
}

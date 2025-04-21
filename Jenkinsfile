pipeline {
  agent {
    node {
      label 'slave-1'
    }

  }
  stages {
    stage('Build') {
      steps {
        bat 'mvn -B -DskipTests clean package'
      }
    }

    stage('Test') {
      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }

      }
      steps {
        bat 'mvn test'
      }
    }

    stage('Sonar-Report') {
      steps {
        bat '''
                    mvn sonar:sonar ^
                    -Dsonar.projectKey=anushka129_webapp ^
                    -Dsonar.organization=anushka129 ^
                    -Dsonar.host.url=https://sonarcloud.io ^
                    -Dsonar.login=cb96c968ac93cfd3ea167f47fb72c7bc9d5ede00
                '''
      }
    }

  }
}
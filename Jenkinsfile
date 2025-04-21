pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
//         stage('Sonar-Report') {
//             steps {
//             sh 'mvn sonar:sonar \
//   -Dsonar.projectKey=jenkins_project \
//   -Dsonar.host.url=http://localhost:9000 \
//   -Dsonar.login=5f09ded7e5db4d0ea0dcfd937c181af706e60475'
//             }
//         }
        stage('Test') { 
            steps {
                bat 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
        stage('Sonar-Report') {
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
}

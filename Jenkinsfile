node {
  stage('Checkout') {
    checkout scm
  }
  stage('Build') {
    sh 'git clean -fdx'
    withMaven(maven: 'Maven 3') {
      sh 'mvn clean verify'
    }
  }
  stage('Reports') {
    junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
  }
}


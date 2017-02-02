node {
  stage('Checkout') {
    checkout scm
  }
  try {
    stage('Build') {
      sh 'git clean -fdx'
      withMaven(maven: 'Maven 3') {
        sh 'mvn clean verify'
      }
    }
  } finally {
    stage('Reports') {
      junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
    }
  }
}


node('maven') {
  stage('Clean') {
    git url: "https://github.com/Matiiii/openshift.git"
    sh "mvn clean"
  }
  
  stage('Build') {
    sh "mvn -DskipTests package"
  }
  
  stage('Test') {
    step {
      sh 'mvn test -Dmaven.test.failure.ignore=true'
          }
    post {
      success {
        junit 'target/surefire-reports/*.xml'
         }
  }
}
}

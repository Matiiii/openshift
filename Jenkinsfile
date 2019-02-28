node('maven') {
  stage('Clean') {
    git url: "https://github.com/Matiiii/openshift.git"
    sh "mvn clean"
  }
  
  stage('Compile') {
    sh "mvn compile"
     }
  
  stage('Install') {
    sh "mvn install"
  }
  
  stage('Package') {
    sh "mvn package"
    stash name:"jar", includes:"target/hello.jar"
  }
  
  stage('Test') {
    parallel(
      "Cart Tests": {
        sh "mvn verify -P cart-tests"
      },
      "Discount Tests": {
        sh "mvn verify -P discount-tests"
      }
    )
  }
}

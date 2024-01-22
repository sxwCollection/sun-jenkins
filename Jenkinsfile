pipeline {
    agent any

    tools {
        maven '3.9.6'
    }
    stages {

    stage ('info'){
      steps {
      echo "---------------------------start build native image---------------"
      sh 'mvn -Pnative spring-boot:build-image -Dimage.name=sxwdocker/sxwrepo01:0.0.1'
      echo "---------------------------end build"}
    }
    }
}

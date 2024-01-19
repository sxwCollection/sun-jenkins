pipeline {

    stages {

    stage ('info'){
      steps {
      echo "---------------------------start info ---------------"
      sh 'mvn -Pnative spring-boot:build-image'
      echo "---------------------------end info"}
    }
    }
}

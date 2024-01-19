pipeline {

    stages {

    stage ('info'){
      steps {
      echo "---------------------------start info ---------------"
      sh 'mvn -Pnative spring-boot:build-image -Dimage.name=myimage:0.0.1'
      echo "---------------------------end info"}
    }
    }
}

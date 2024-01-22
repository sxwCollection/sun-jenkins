pipeline {
    agent any

    tools {
        maven '3.9.6'
    }
    environment {
        DOCKERHUB_CREDENTIALS= credentials('sun-docker-hub') 
    }
    stages {

    stage ('build spring native image'){
      steps {
      echo "---------------------------start build native image---------------"
      sh 'mvn -Pnative spring-boot:build-image -Dimage.name=sxwdocker/sxwrepo01:0.0.1'
      echo "---------------------------end build"}
    }
    stage('docker login'){
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'                		
	echo 'Login Completed'  
            }
        }
    stage('docker push'){
            steps {
                sh 'docker push sxwdocker/sxwrepo01:0.0.1'  
            }
        }       
        
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}

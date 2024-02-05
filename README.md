# sun-jenkis
# what
in this demo it is shown:  
1. how to install Jenkins  
2. how to set up maven in Jenkins  
1. how to create a Jenkins docker agent  
1. how to connect Jenkins with Dockerhub  
1. how to use a multibranch pipeline to build a project, build an OCI image and to push to a docker hube repo  

# how to
## install Jenkins
1 if Java is installed, the war file of a Jenkins release package could be downloaded and executed:  
java -jar jenkins.war  
2 docker and dind (docker in docker) way:  
which is described in https://www.jenkins.io/doc/book/installing/docker/#setup-wizard  
and run with  
docker run --name jenkins-docker --detach  
--privileged --network jenkins --network-alias docker  
--env DOCKER_TLS_CERTDIR=/certs  
--volume jenkins-docker-certs:/certs/client  
--volume jenkins-data:/var/jenkins_home  
--publish 2376:2376  
docker:dind --storage-driver overlay2    

docker start jenkins-blueocean, docker start jenkins-docker
docker stop jenkins-blueocean, docker stop jenkins-docker

## setup maven
add maven in Manage Jenkins/ Tools like:  
![maven](/img/maven.png)  
to use the maven in Jenkinsfile:  
pipeline {  
    tools {  
        maven '3.9.6'  
    }   

## docker agent 
there two ways to connect Jenkins with docker:  
1. share the docker.sock  
enable docker remote API  
edit /lib/systemd/system/docker.service  
set:  
ExecStart=/usr/bin/dockerd -H=fd:// -H=tcp://0.0.0.0:4243   

1. dind with jenkins agent running, if Jenkins is installed with dind way, it is all set up.  

## connect to dockerhub  

1. add docker access token in Dockerhub user/account settings/security/new access token  
2. add a global credentials in manage jenkins/credentials/system/ global credentials, like  
3. , it could also be project scoped, 


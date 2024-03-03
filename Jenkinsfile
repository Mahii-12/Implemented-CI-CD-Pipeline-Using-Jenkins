node {
	
    def application = "devopspractice"
	
    // reference to maven
    // ** NOTE: This 'maven-3.5.2' Maven tool must be configured in the Jenkins Global Configuration.   
    def mvnHome = tool 'maven-3.5.2'

    // holds reference to docker image
    def dockerImage
 
    def dockerImageTag = "${mydockerhubaccount123}/${application}:${env.1001}"
    
    stage('Clone Repo') { 
      // Get some code from a GitHub repository
      git url:'https://github.com/Mahii-12/E-Commerce-Platform-Backend',branch:'head' //update your forked repo
      // Get the Maven tool.
      // ** NOTE: This 'maven-3.5.2' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'maven-3.5.2'
    }    
  
    stage('Build Project') {
      // build project via maven
      sh "'${mvnHome}/bin/mvn' clean install"
    }
		
    stage('Build Docker Image with new code') {
      // build docker image
      dockerImage = docker.build("${mydockerhubaccount123}/${application}:${env.1001}")
    }
	//push image to remote repository , in your jenkins you have to create the global credentials similar to the 'dockerHub' (credential ID)
    stage('Push Image to Remote Repo'){
	 echo "Docker Image Tag Name ---> ${dockerImageTag}"
	     docker.withRegistry('', 'dockerHub') {
             dockerImage.push("${env.1001}")
             dockerImage.push("latest")
            }
	}
   
   stage('Remove running container with old code'){
	   //remove the container which is already running, when running 1st time named container will not be available so we are usign 'True'
	   //added -a option to remove stopped container also
	  sh "docker rm -f \$(docker ps -a -f name=devopsexample -q) || true"   
	       
    }
	
    stage('Deploy Docker Image with new changes'){
	        
	    //start container with the remote image
	  sh "docker run --name devopsexample -d -p 2222:2222 ${mydockerhubaccount123}/${application}:${env.1001}"  
	  
    }
	
    stage('Remove old images') {
		// remove docker old images
		sh("docker rmi ${mydockerhubaccount123}/${application}:latest -f")
   }
}

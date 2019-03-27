pipeline {
    agent any
	
    def mvnHome
    mvnHome = tool name: 'maven354', type: 'maven'
    stages {
        stage('GIT Checkout') {
	    steps {
		 echo 'Initiating GIT Checkout...'
		 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/agupta2411/JavaProject_Maven.git']]])
		 echo 'GIT checkout completed...!!!'
	    }
	}

	stage('Build') {
            steps {
                echo 'Starting the Building phase...'
		 if (isUnix()) {
       
			sh "'${mvnHome}\\bin\\mvn' compile"
	  
       } 
		 else  {
 
          
       	bat script: "${mvnHome}\\bin\\mvn compile"
 
	         }
		
		echo 'Building the project completed successfully...!'
		
            }
        }

        stage('Test') {
            steps {
                echo 'Starting the Testing phase...'
		if (isUnix()) {
       
			sh "'${mvnHome}\\bin\\mvn' test"
	  
       } 
		 else  {
 
          
       	bat script: "${mvnHome}\\bin\\mvn test"
 
	         }
		
		echo 'Testing of the project completed successfully...!'
		
            }
        }

	stage('Package') {
            steps {
                echo 'Packaging of the project begins...'
		if (isUnix()) {
       
			sh "'${mvnHome}\\bin\\mvn' package"
	  
       } 
		 else  {
 
          
       	bat script: "${mvnHome}\\bin\\mvn package"
 
	         }
		
		echo 'Successfully completed packaging of the project...!'
		
            }
        }

        stage('Deploy') {
            steps {
                echo 'Ready to deploy the packaged files....'
		if (isUnix()) {
       
			sh "'${mvnHome}\\bin\\mvn' deploy"
	  
       } 
		 else  {
 
          
       	bat script: "${mvnHome}\\bin\\mvn deploy"
 
	         }
		
		echo 'Deployment of the packaged files completed successfully...!'
            }
        }
    }
}

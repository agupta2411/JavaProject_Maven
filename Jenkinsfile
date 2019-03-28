pipeline {
    agent any
	
    tools {
	maven 'maven354'
    }

    //def mvnHome
    //mvnHome = tool name: 'maven354', type: 'maven'

    stages {
        stage('GIT Checkout') {
	    steps {
		 echo '**********Initiating GIT Checkout...**********'
		 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/agupta2411/JavaProject_Maven.git']]])
		 echo '**********GIT checkout completed...!!!**********'
	    }
	}

	stage('Build') {
           steps {
                echo '**********Starting the Building phase...**********'
		
			script {
				if (isUnix()) {
       
					sh 'mvn clean compile'
	        		} 
				else  {
 
          
       			bat script: "mvn clean compile"
 
	        		}
		  	 	echo '**********Building the project completed successfully...!**********'
			}
		}
        }



	//	 when {
        //		expression {
        //    			return isUnix()
       	//		 }
	//	}
	//	
	//	step {
	//		sh 'mvn compile'
	//	}

    
		  



            

        stage('Test') {
            steps {
                echo '**********Starting the Testing phase...**********'
		   script  {
				if (isUnix()) {
       
					sh 'mvn test'
	  
       		} 
		 		else  {
 
          
       			bat script: "mvn test"
 
	         		}
				
				echo '**********Testing of the project completed successfully...!**********'
		  }
            }
        }


	stage('Package') {
            steps {
                echo '**********Packaging of the project begins...**********'
		   script {
				if (isUnix()) {
       
					sh 'mvn package'
	  
       		} 
		 		else  {
 
          
       			bat script: "mvn package"
 
	         		}
		
				echo '**********Successfully completed packaging of the project...!**********'
		}
            }		
        }
	    
	   // stage('Execute') {
	//	steps {
	     //		echo '**********Executing the Java Project...**********'
	     //		java -jar target/demo-project-3.0-SNAPSHOT.jar
	     //		echo '**********Java project executed successfully...***********'	
		//}
	//}

        stage('Deploy') {
            steps {
                echo '**********Ready to deploy the packaged files....**********'
			script {
				if (isUnix()) {
       
					sh 'mvn deploy'
	  
       		} 
				 else  {
 
          
       			bat script: "mvn deploy"
 
	        		 }
		
				echo '**********Deployment of the packaged files completed successfully...!**********'
			}
            }
        }
    }
}

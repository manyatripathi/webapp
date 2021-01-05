@Library('multi@master') _

node 
{
   def MAVEN_HOME = tool "Maven_HOME"
   def JAVA_HOME = tool "JAVA_HOME"
   env.techStack = "java"
   env.PATH="${env.PATH};${MAVEN_HOME}\\bin;${JAVA_HOME}\\bin"
   try{
	   stage('hvhb'){	bat "git config --global http.sslVerify false"}
   stage('Checkout')
   {
       FAILED_STAGE=env.STAGE_NAME
        gitCheckout(
                branch: "master",
                url: "https://github.com/manyatripathi/webapp.git"
                )
   }

   stage('Initial Setup')
   {   
       initialSetup()
   }

   
   }
	catch(e){
		echo "Pipeline has failed"
		//emailext body: "${env.BUILD_URL} has result ${currentBuild.result} at stage ${FAILED_STAGE} with error" + e.toString(), subject: "Failure of pipeline: ${currentBuild.fullDisplayName}", to: "${mailrecipient}"
	    throw e
	
	}
	     
}


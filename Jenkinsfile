pipeline {
  agent any
  tools {nodejs "nodejs"}
	    
	stages {   
     stage('Install dependencies') {
		steps {
			sh 'npm install'
			}
			}
										           
			stage('Angular Build') {
			steps {
			sh 'node_modules/.bin/ng build --prod'
			}
			}
     stage("Publish to Azure") {
            steps {
            azureWebAppPublish appName: "angularapp-jenkins",
            azureCredentialsId: "springbootapp-sp",
            publishType: "file",
            filePath: "**/*",
            resourceGroup: "VstsRG-ems-test-ed0a",
            sourceDirectory: "."
            }
        }		
		    }
}

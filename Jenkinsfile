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
      stage('deploy') {
      def resourceGroup = 'VstsRG-ems-test-ed0a'
      def webAppName = 'angular-app-sample'
      azureWebAppPublish azureCredentialsId: 'springbootapp-sp', publishType: 'file',
      resourceGroup: resourceGroup, appName: webAppName,
      filePath: '**/*', sourceDirectory: 'target', targetDirectory: 'webapps'
              }			
		    }
}

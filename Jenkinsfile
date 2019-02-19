node('master') {
	    
	            
	              
	              def AppUrl
	              def TerrPath
	              def ArtifactoryPath
	              def UserName
	              def Password	
	              TerrPath=props.TerraformPAth
	                             def props_path="props_dir"
	                             
	                             dir(props_path) {
	                             
	                                           stage ('Prop Checkout ') {
	                                           
	                                                          git 'https://github.com/Laxmi007/Util.git'
	                                                          
	                                                          def props = readProperties file: 'PropertiesFile.properties'
	                                                          
	                                                          AppUrl=props.GIT_URL
	                                                     ArtifactoryPath =props.Artifactory_ID
	                                                     UserName=props.username
	                                                     Password=props.Password
	                           
	                                           }
	                             }
							
				stage('App Checkout ') {
	                        	     	echo "${AppUrl}"
	                             		git "${AppUrl}"
	                 
				}
				stage('Code Analysis' ) {
	                                           sh 'mvn sonar:sonar'
	                        }
				stage('Build Automation') {    
	                                           sh 'mvn clean package'
	                        }
				stage('Build Management'){
	                                          def server = Artifactory.newServer url:ArtifactoryPath, username: UserName, password: Password
	                                          def uploadSpec = """{
	                                           "files": [
	                                                {
	                                                         "pattern": "*.war",
	                                                         "target": "lib-staging"
	                                                }
	                                             ]
	                                          }"""
	                        }
				stage('Deployment'){
						sh 'sudo cp target/*.war /home/devopsuser7/apache-tomcat-8.5.37/webapps'
						sh 'sudo ls -ltr /home/devopsuser7/apache-tomcat-8.5.37/webapps'
	                        }
			
		notify('Project Build Completed ') 

}

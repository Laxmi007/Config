node('master') {
	    
	              notify('Project Build Started')
	              
	              def AppUrl
	              def TerrPath
	              def ArtifactoryPath
	              def UserName
	              def Password	
	              
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
								 }

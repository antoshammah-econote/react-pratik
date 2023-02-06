pipeline {
    agent {
        label 'master'
    }
    stages {
        stage('Installing Dependencies') { 
			agent {
				label 'Device_Node'
			}
            steps {
                //cleanWs()
                //sh "sudo rm -rf node_modules/ build/"
                //sh 'npm install'
				//sh 'sudo npm install --force'
				sh "sudo npm i --unsafe-perm"
            }
        }
		stage('Build') { 
			agent {
				label 'Device_Node'
			}
            steps {
				sh 'sudo yarn install'
				//sh 'sudo yarn add react-epub-viewer'
				//sh 'sudo yarn add styled-components'
				//sh 'sudo yarn add @material-ui/core'
				//sh 'npm cache clean --force'
                //sh 'sudo npm run build'
				//sh 'sudo systemctl restart jenkins'
                //sh 'zip -r build.zip build'
                //script{
				//	withAWS(credentials: 'awsCreds') {
				//		s3Upload(file:"build.zip", bucket:'reactjs-builds', path:"")
				//		}
				//}
                //sh 'tar -zvcf build.tar.gz build'
                //stash includes: "build/**/*", name: 'build' 
                //stash includes: "node_modules/**/*", name: 'nodeModules' 
                //cleanWs()
            }
        }
		stage('Deploy') { 
			agent {
				label 'Device_Node'
			}
            steps {
               script{
					def statusCode = sh (
						script: "sudo kill -9 \$(sudo lsof -t -i:3000)",
						returnStatus: true
					)
                //   sh 'sudo rm -rf build node_modules'
                //    unstash 'nodeModules'
                //    unstash 'build'
					
					sh """
                        #!/bin/bash
                         sudo npm run start &
                    """
					
                }
            }
        }
    }
}

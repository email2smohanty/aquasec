// properties([[$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false],
// 	parameters([
// 	string(defaultValue: 'aquasec', description: 'Application git repo', name: 'APP_Git_Repo'),
// 	string(defaultValue: 'master', description: 'Application git branch', name: 'APP_Git_Branch'),
// 	string(defaultValue: 'email2smohanty', description: 'Docker hub name for pushing docker image', name: 'Dockerhub_Name'),
// 	string(defaultValue: 'aquasec', description: 'Image name', name: 'Image_Name'),
// 	string(defaultValue: 'latest', description: 'Image tag', name: 'Image_Tag')])
// 	])

node{

    stage('Building And Pushing Image') {
  		try {
                        sh 'rm -rf aquasec'
			sh 'git clone -b main https://github.com/email2smohanty/aquasec.git'
                  

			//Build docker image
            dir("aquasec/") {
                  sh "docker build -t email2smohanty/aquasec:latest ."
           }

			//Push image to artifactory
			sh "docker push email2smohanty/aquasec:latest"
  			
  	  	} catch (e) {
  			println(e.toString())
  			println(e.getMessage())
        }
	}
}

properties([[$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false],
	parameters([
	string(defaultValue: 'aquasec', description: 'Application git repo', name: 'APP_Git_Repo'),
	string(defaultValue: 'master', description: 'Application git branch', name: 'APP_Git_Branch'),
	string(defaultValue: 'email2smohanty', description: 'Docker hub name for pushing docker image', name: 'Dockerhub_Name'),
	string(defaultValue: 'aquasec', description: 'Image name', name: 'Image_Name'),
	string(defaultValue: 'latest', description: 'Image tag', name: 'Image_Tag')])
	])

node{

    stage('Building And Pushing Image') {
  		try {
  
			sh 'git clone -b ${APP_Git_Branch} https://github.com/email2smohanty/${APP_Git_Repo}.git'
                  

			//Build docker image
            dir("${APP_Git_Repo}/") {
                  sh "docker build -t ${Dockerhub_Name}/${Image_Name}:${Image_Tag} ."
           }

			//Push image to artifactory
			sh "docker push ${Dockerhub_Name}/${Image_Name}:${Image_Tag} ."
  			
  	  	} catch (e) {
  			println(e.toString())
  			println(e.getMessage())
        }
	}
}

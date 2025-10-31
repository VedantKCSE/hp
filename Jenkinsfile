pipeline {
    agent any
    environment{
      	DOCKER_IMAGE='heloo-py:1.0' //Docker Image Name
    }
    stages {
        stage('Checkout') {
            steps {
                	git branch: 'main', url 'https://github.com/VedantKCSE/hp.git'
            }
        }
        stage('Docker Build'){
            steps {
                script {
                  	//Check if Docker File Exist
										if(fileExists('DockerFile')){
											sh "docker build -t ${DOCKER_IMAGE} ."
										} else {
											error "Dockerfile not found in WS. ❌"
										}
                }
            }
        }
				stage('Docker Run (Optional)'){
					steps {
						sh "docker run ${DOCKER_IMAGE}"
					}
				}
    }
	post {
		success {
			echo 'Python appln Docker image Built. 🚀'
		}
		failure {
			echo 'Docker Buil or Run Failed. 🚒'
		}
	}
}

pipeline {
    environment {
    
    image_name = "anchal72/test"
    docker_image = ''
    
    }
    agent any

    stages {
        stage('Build') {
            agent {
            	dockerfile true
            }
            steps {
    	        echo "Building..."
	    }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                script {
		   docker.withRegistry("https://hub.docker.com",'docker_hub')
		   docker_image.push("$BUILD_NUMBER")
                   docker_image.push('latest')
		}
            }
        }
    }
}

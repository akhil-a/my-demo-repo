node('wfh') {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("akhilanil10/test_alpine1")
    }

    stage('Test image') {
        
        app.inside {
            echo "Tests passed"
        }
	docker.image('akhilanil10/test_alpine1:latest').inside {
		sh 'pwd'
	}
    }

    stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account
		*/
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-id') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
            } 
                echo "Trying to Push Docker Build to DockerHub"
    }
}
node {
	stage('trial') {
		echo "Hi Hello"
	}
}

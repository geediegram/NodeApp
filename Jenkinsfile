
node {

    def app

    stage('Clone Repository') {
        /* Cloning the Repository to our Workspace */

        git credentialsId: 'github', 
        url: 'https://github.com/Adebola-Semicolon/NodeApp.git'
        
    }

    stage('Build image') {
	    
       sh('docker build -t 88337744666/node-app:2.0 .')
    }

    stage('Login into Docker Hub') {
        withCredentials([string(credentialsId: 'docker-hub-pwd', variable: 'docker-Pwd')]) {
        }
	    
        sh("docker login -u 88337744666 -p ${docker-Pwd}")
    }

    stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account
		*/
//         docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
//             app.push("${env.BUILD_NUMBER}")
//             app.push("latest")
//             } 
//                 echo "Trying to Push Docker Build to DockerHub"
	    sh('docker push 88337744666/node-app:2.0')
    }
	
    stage('Deploy Node-App Container ') {
	    
        sh('docker run -d -p 8000:8000 88337744666/node-app:2.0')
    }

}

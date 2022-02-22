node {
    stage('Clone Repository') {  
        checkout scm   
    }
    stage('Build Image') {   
        def customImage = docker.build("vishaljain088/dockerwebapp")
    }
    stage('Push Image') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerHub') {
        /* Push the container to the custom Registry */
        customImage.push()
        }
    }
}

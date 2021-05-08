node ('Ubuntu-App-Server-Agent'){  
    def app
    stage('Cloning Git') {
        /* Let's make sure we have the repository cloned to our workspace */
       checkout scm
    }  
    
    stage('Build-and-Tag') {
        app = docker.build("reni2study/snake")
    /* This builds the actual image; synonymous to
         * docker build on the command line */
        //app = docker.build("amrit96/snake")
    }
    stage('Post-to-dockerhub') {
    
     docker.withRegistry('https://registry.hub.docker.com', 'reni2study') {
            app.push("latest")
        			}
         }
    
    stage('Pull-image-server') {
         sh "docker-compose down"
         sh "docker-compose up -d"
      }
    
}

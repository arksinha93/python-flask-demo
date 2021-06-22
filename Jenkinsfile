node {
      
      stage('Get Source') {
      // copy source code from local file system and test
      // for a Dockerfile to build the Docker image
      //sshagent (credentials: ['arksinha']) {
      git ('https://github.com/arksinha93/python-flask-demo.git')
      if (!fileExists("Dockerfile")) {
         error('Dockerfile missing.')
      }
   }
      
   stage('Build Docker') {
       // build the docker image from the source code using the BUILD_ID parameter in image name
         sh "sudo docker build -t my-flask-app ."
         sh "sudo docker rm --force my-flask-app"
   }
      
   stage('Test and Deploy Docker Container'){
         //sh "sudo docker tag my-flask-app:latest arksinha/flaskapp:latest"
         //sh "sudo docker pull arksinha/flaskapp"
          sh "sudo docker run -p 5000:5000 --name my-flask-app -d my-flask-app"      
    }
}

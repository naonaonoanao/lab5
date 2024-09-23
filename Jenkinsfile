node ('agent1') {
  def app
  stage('Cloning Git') {
    checkout scm
  }
  stage('Build-and-Tag') {
    app = docker.build("naonao69/lab5")
  }
  stage('Post-to-dockerhub') {
    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub_creds') {
      def app = docker.build("egorovanasta226@gmail.com/lab5")
      app.push("latest")
    }
  }
  stage('Pull-image-server') {
    sh "docker-compose down"
    sh "docker-compose up -d"
  }
}

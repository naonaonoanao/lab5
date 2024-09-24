node ('agent1') {
  def app
  stage('Cloning Git') {
    checkout scm
  }
  stage('Build-and-Tag') {
    app = docker.build("naonao69/lab5")
  }
  stage('Post-to-dockerhub') {
    docker.withRegistry('https://registry.hub.docker.com', 'b38da23d-c317-451c-81c5-44ff2eda94b1') {
      app.push("latest")
    }
  }
  stage('Pull-image-server') {
    sh "docker-compose down"
    sh "docker-compose up -d"
  }
}

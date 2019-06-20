node {
  def app

  stage("Clone repository"){
    /* clone the repository */
    checkout scm
  }

  stage("Permissions"){
    /* change direction */
    sh "cd AdminServer"
    /* set maven wrapper permissions */
    sh "chmod 711 ./mvnw"
  }

  stage("Test"){
    /* run tests */
    sh "./mvnw test"
  }

  stage("Build Project"){
    /* build the project */
    sh "./mvnw clean install"
  }

  stage("Build Image"){
    app = docker.build("digidarkdev/admin-server")
  }

  stage("Push Image"){
    /* push the image to docker hub */
    sh "echo TODO"
  }


}
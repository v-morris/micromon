node {
  def app

  stage("Clone repository"){
    /* clone the repository */
    checkout scm
  }

  stage("Permissions"){
    // change directory
    dir("AdminServer"){
      // set maven wrapper permissions
      sh "chmod 711 ./mvnw"
    }
    
  }

  stage("Test"){
    /* run tests */
    dir("AdminServer"){
      sh "./mvnw test"
    }
  }

  stage("Build Project"){
    dir("AdminServer"){
    /* build the project */
      sh "./mvnw clean install"
    }
  }
  
  stage("Build Image"){
    dir("AdminServer"){
      app = docker.build("digidarkdev/admin-server")
    }
  }

  stage("Push Image"){
    /* push the image to docker hub */
    sh "echo TODO"
  }


}
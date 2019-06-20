node {
  def app
  def app2

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

    dir("DiscoveryServer"){
      // set maven wrapper permissions
      sh "chmod 711 ./mvnw"
    }
    
  }

  stage("Test"){
    /* run tests */
    dir("AdminServer"){
      sh "./mvnw test"
    }

    dir("DiscoveryServer"){
      sh "./mvnw test"
    }
  }

  stage("Build Project"){
    dir("AdminServer"){
    /* build the project */
      sh "./mvnw clean install"
    }

    dir("DiscoveryServer"){
    /* build the project */
      sh "./mvnw clean install"
    }
  }

  stage("Build Image"){
    dir("AdminServer"){
      app = docker.build("digidarkdev/admin-server")
    }

    dir("DiscoveryServer"){
      app2 = docker.build("digidarkdev/discovery-server")
    }
  }


  
stage("Push Image") {
      when {
        branch "master"
      }
      steps {
        withDockerRegistry([ credentialsId: "docker-hub-credentials", url: "https://registry.hub.docker.com" ]) {
          sh "docker push digidarkdev/AdminServer:latest"
          sh "docker push digidarkdev/DiscoveryServer:latest"
        }
      }
    }

  // stage("Push Image"){
    
  //   dir("AdminServer"){
  //     /* push the image to docker hub */
  //     docker.withRegistry("https://registry.hub.docker.com", "docker-hub-credentials"){
  //       app.push("${env.BUILD_NUMBER}")
  //       app.push("latest")
  //     }
  //   }

  //   dir("DiscoveryServer"){
  //     /* push the image to docker hub */
  //     docker.withRegistry("https://registry.hub.docker.com", "docker-hub-credentials"){
  //       app.push("${env.BUILD_NUMBER}")
  //       app.push("latest")
  //     }
  //   }
  // }













}